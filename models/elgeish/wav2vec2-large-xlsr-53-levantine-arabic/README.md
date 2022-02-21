---
language: ar
datasets:
- arabic_speech_corpus
tags:
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
---

# Wav2Vec2-Large-XLSR-53-Arabic

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53)
on the [Arabic Speech Corpus dataset](https://huggingface.co/datasets/arabic_speech_corpus).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import librosa
import torch
from datasets import load_dataset
from lang_trans.arabic import buckwalter
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

dataset = load_dataset("arabic_speech_corpus", split="test")  # "test[:n]" for n examples
processor = Wav2Vec2Processor.from_pretrained("elgeish/wav2vec2-large-xlsr-53-arabic")
model = Wav2Vec2ForCTC.from_pretrained("elgeish/wav2vec2-large-xlsr-53-arabic")
model.eval()

def prepare_example(example):
    example["speech"], _ = librosa.load(example["file"], sr=16000)
    example["text"] = example["text"].replace("-", " ").replace("^", "v")
    example["text"] = " ".join(w for w in example["text"].split() if w != "sil")
    return example

dataset = dataset.map(prepare_example, remove_columns=["file", "orthographic", "phonetic"])

def predict(batch):
    inputs = processor(batch["speech"], sampling_rate=16000, return_tensors="pt", padding="longest")
    with torch.no_grad():
        predicted = torch.argmax(model(inputs.input_values).logits, dim=-1)
    predicted[predicted == -100] = processor.tokenizer.pad_token_id  # see fine-tuning script
    batch["predicted"] = processor.tokenizer.batch_decode(predicted)
    return batch

dataset = dataset.map(predict, batched=True, batch_size=1, remove_columns=["speech"])

for reference, predicted in zip(dataset["text"], dataset["predicted"]):
    print("reference:", reference)
    print("predicted:", predicted)
    print("reference (untransliterated):", buckwalter.untrans(reference))
    print("predicted (untransliterated):", buckwalter.untrans(predicted))
    print("--")
```

Here's the output:

```
reference: >atAHat lilbA}iEi lmutajaw~ili >an yakuwna jA*iban lilmuwATini l>aqal~i daxlan
predicted: >ataAHato lilobaA}iEi Alomutajaw~ili >ano yakuwna jaA*ibAF lilomuwaATini Alo>aqal~i daxolAF
reference (untransliterated): أَتاحَت لِلبائِعِ لمُتَجَوِّلِ أَن يَكُونَ جاذِبَن لِلمُواطِنِ لأَقَلِّ دَخلَن
predicted (untransliterated): أَتَاحَتْ لِلْبَائِعِ الْمُتَجَوِّلِ أَنْ يَكُونَ جَاذِباً لِلْمُوَاطِنِ الْأَقَلِّ دَخْلاً
--
reference: >aHrazat muntaxabAtu lbarAziyli wa>lmAnyA waruwsyA fawzan fiy muqAbalAtihim l<iEdAdiy~api l~atiy >uqiymat istiEdAdan linihA}iy~Ati ka>si lEAlam >al~atiy satanTaliqu baEda >aqal~i min >usbuwE
predicted: >aHorazato munotaxabaAtu AlobaraAziyli wa>alomaAnoyaA waruwsoyaA fawozAF fiy muqaAbalaAtihimo >aliEodaAdiy~api Al~atiy >uqiymat AsotiEodaAdAF linahaA}iy~aAti ka>osi AloEaAlamo >al~atiy satanoTaliqu baEoda >aqal~i mino >usobuwEo
reference (untransliterated): أَحرَزَت مُنتَخَباتُ لبَرازِيلِ وَألمانيا وَرُوسيا فَوزَن فِي مُقابَلاتِهِم لإِعدادِيَّةِ لَّتِي أُقِيمَت ِستِعدادَن لِنِهائِيّاتِ كَأسِ لعالَم أَلَّتِي سَتَنطَلِقُ بَعدَ أَقَلِّ مِن أُسبُوع
predicted (untransliterated): أَحْرَزَتْ مُنْتَخَبَاتُ الْبَرَازِيلِ وَأَلْمَانْيَا وَرُوسْيَا فَوْزاً فِي مُقَابَلَاتِهِمْ أَلِعْدَادِيَّةِ الَّتِي أُقِيمَت اسْتِعْدَاداً لِنَهَائِيَّاتِ كَأْسِ الْعَالَمْ أَلَّتِي سَتَنْطَلِقُ بَعْدَ أَقَلِّ مِنْ أُسْبُوعْ
--
reference: >axfaqa majlisu ln~uw~Abi ll~ubnAniy~u fiy xtiyAri ra}iysin jadiydin lilbilAdi xalafan lilr~a}iysi lHAliy~i l~a*iy tantahiy wilAyatuhu fiy lxAmisi wAlEi$riyn min mAyuw >ayAra lmuqbil
predicted: >axofaqa majolisu Aln~uw~aAbi All~ubonaAniy~u fiy AxotiyaAri ra}iysK jadiydK lilobilaAdi xalafAF lilr~a}iysi AloHaAliy~i Al~a*iy tanotahiy wilaAyatuhu fiy AloxaAmisi waAloEi$oriyno mino maAyuw >ay~aAra Alomuqobilo
reference (untransliterated): أَخفَقَ مَجلِسُ لنُّوّابِ للُّبنانِيُّ فِي ختِيارِ رَئِيسِن جَدِيدِن لِلبِلادِ خَلَفَن لِلرَّئِيسِ لحالِيِّ لَّذِي تَنتَهِي وِلايَتُهُ فِي لخامِسِ والعِشرِين مِن مايُو أَيارَ لمُقبِل
predicted (untransliterated): أَخْفَقَ مَجْلِسُ النُّوَّابِ اللُّبْنَانِيُّ فِي اخْتِيَارِ رَئِيسٍ جَدِيدٍ لِلْبِلَادِ خَلَفاً لِلرَّئِيسِ الْحَالِيِّ الَّذِي تَنْتَهِي وِلَايَتُهُ فِي الْخَامِسِ وَالْعِشْرِينْ مِنْ مَايُو أَيَّارَ الْمُقْبِلْ
--
reference: <i* sayaHDuru liqA'a ha*A lEAmi xamsun wavalAvuwna minhum
predicted: <i*o sayaHoDuru riqaA'a ha*aA AloEaAmi xamosN wa valaAvuwna minohumo
reference (untransliterated): إِذ سَيَحضُرُ لِقاءَ هَذا لعامِ خَمسُن وَثَلاثُونَ مِنهُم
predicted (untransliterated): إِذْ سَيَحْضُرُ رِقَاءَ هَذَا الْعَامِ خَمْسٌ وَ ثَلَاثُونَ مِنْهُمْ
--
reference: >aElanati lHukuwmapu lmiSriy~apu Ean waqfi taqdiymi ld~aEmi ln~aqdiy~i limuzAriEiy lquTni <iEtibAran mina lmuwsimi lz~irAEiy~i lmuqbil
predicted: >aEolanati AloHukuwmapu AlomiSoriy~apu Eano waqofi taqodiymi Ald~aEomi Aln~aqodiy~i limuzaAriEiy AloquToni <iEotibaArAF mina Alomuwsimi Alz~iraAEiy~i Alomuqobilo
reference (untransliterated): أَعلَنَتِ لحُكُومَةُ لمِصرِيَّةُ عَن وَقفِ تَقدِيمِ لدَّعمِ لنَّقدِيِّ لِمُزارِعِي لقُطنِ إِعتِبارَن مِنَ لمُوسِمِ لزِّراعِيِّ لمُقبِل
predicted (untransliterated): أَعْلَنَتِ الْحُكُومَةُ الْمِصْرِيَّةُ عَنْ وَقْفِ تَقْدِيمِ الدَّعْمِ النَّقْدِيِّ لِمُزَارِعِي الْقُطْنِ إِعْتِبَاراً مِنَ الْمُوسِمِ الزِّرَاعِيِّ الْمُقْبِلْ
--
reference: >aElanat wizArapu lSi~Ha~pi lsa~Euwdiya~pu lyawma Ean wafAtayni jadiydatayni biAlfayruwsi lta~Ajiyi kuwruwnA nuwfil
predicted: >aEolanato wizaArapu AlS~iH~api Als~aEuwdiy~apu Aloyawoma Eano wafaAtayoni jadiydatayoni biAlofayoruwsi Alt~aAjiy kuwruwnaA nuwfiylo
reference (untransliterated): أَعلَنَت وِزارَةُ لصِّحَّةِ لسَّعُودِيَّةُ ليَومَ عَن وَفاتَينِ جَدِيدَتَينِ بِالفَيرُوسِ لتَّاجِيِ كُورُونا نُوفِل
predicted (untransliterated): أَعْلَنَتْ وِزَارَةُ الصِّحَّةِ السَّعُودِيَّةُ الْيَوْمَ عَنْ وَفَاتَيْنِ جَدِيدَتَيْنِ بِالْفَيْرُوسِ التَّاجِي كُورُونَا نُوفِيلْ
--
reference: <iftutiHati ljumuEapa faE~Aliy~Atu ld~awrapi lr~AbiEapa Ea$rapa mina lmihrajAni ld~awliy~i lilfiylmi bimur~Aki$
predicted: <ifotutiHapi AlojumuwEapa faEaAliyaAtu Ald~aworapi Alr~aAbiEapa Ea$orapa miyna AlomihorajaAni Ald~awoliy~i lilofiylomi bimur~Aki$
reference (untransliterated): إِفتُتِحَتِ لجُمُعَةَ فَعّالِيّاتُ لدَّورَةِ لرّابِعَةَ عَشرَةَ مِنَ لمِهرَجانِ لدَّولِيِّ لِلفِيلمِ بِمُرّاكِش
predicted (untransliterated): إِفْتُتِحَةِ الْجُمُوعَةَ فَعَالِيَاتُ الدَّوْرَةِ الرَّابِعَةَ عَشْرَةَ مِينَ الْمِهْرَجَانِ الدَّوْلِيِّ لِلْفِيلْمِ بِمُرّاكِش
--
reference: >ak~adat Ea$ru duwalin Earabiy~apin $Arakati lxamiysa lmADiya fiy jtimAEi jd~ap muwAfaqatahA EalY l<inDimAmi <ilY Hilfin maEa lwilAyAti lmut~aHidapi li$an~i Hamlapin Easkariy~apin munas~aqapin Did~a tanZiymi >ald~awlapi l<islAmiy~api
predicted: >ak~adato Ea$oru duwalK Earabiy~apK $aArakapiy Aloxamiysa AlomaADiya fiy AjotimaAEi jad~ap muwaAfaqatahaA EalaY Alo<inoDimaAmi <ilaY HilofK maEa AlowilaAyaAti Alomut~aHidapi li$an~i HamolapK Easokariy~apK munas~aqapK id~a tanoZiymi Ald~awolapi Alo<isolaAmiy~api
reference (untransliterated): أَكَّدَت عَشرُ دُوَلِن عَرَبِيَّةِن شارَكَتِ لخَمِيسَ لماضِيَ فِي جتِماعِ جدَّة مُوافَقَتَها عَلى لإِنضِمامِ إِلى حِلفِن مَعَ لوِلاياتِ لمُتَّحِدَةِ لِشَنِّ حَملَةِن عَسكَرِيَّةِن مُنَسَّقَةِن ضِدَّ تَنظِيمِ أَلدَّولَةِ لإِسلامِيَّةِ
predicted (untransliterated): أَكَّدَتْ عَشْرُ دُوَلٍ عَرَبِيَّةٍ شَارَكَةِي الْخَمِيسَ الْمَاضِيَ فِي اجْتِمَاعِ جَدَّة مُوَافَقَتَهَا عَلَى الْإِنْضِمَامِ إِلَى حِلْفٍ مَعَ الْوِلَايَاتِ الْمُتَّحِدَةِ لِشَنِّ حَمْلَةٍ عَسْكَرِيَّةٍ مُنَسَّقَةٍ ِدَّ تَنْظِيمِ الدَّوْلَةِ الْإِسْلَامِيَّةِ
--
reference: <iltaHaqa luwkA ziydAna <ibnu ln~ajmi ld~awliy~i lfaransiy~i ljazA}iriy~i l>Sli zayni ld~iyni ziydAn biAlfariyq
predicted: <ilotaHaqa luwkaA ziydaAna <ibonu Aln~ajomi Ald~awoliy~i Alofaranosiy~i AlojazaA}iriy~i Alo>aSoli zayoni Ald~iyni zayodaAno biAlofariyqo
reference (untransliterated): إِلتَحَقَ لُوكا زِيدانَ إِبنُ لنَّجمِ لدَّولِيِّ لفَرَنسِيِّ لجَزائِرِيِّ لأصلِ زَينِ لدِّينِ زِيدان بِالفَرِيق
predicted (untransliterated): إِلْتَحَقَ لُوكَا زِيدَانَ إِبْنُ النَّجْمِ الدَّوْلِيِّ الْفَرَنْسِيِّ الْجَزَائِرِيِّ الْأَصْلِ زَيْنِ الدِّينِ زَيْدَانْ بِالْفَرِيقْ
--
reference: >alma$Akilu l~atiy yatrukuhA xalfahu dA}iman
predicted: Aloma$aAkilu Al~atiy yatorukuhaA xalofahu daA}imAF
reference (untransliterated): أَلمَشاكِلُ لَّتِي يَترُكُها خَلفَهُ دائِمَن
predicted (untransliterated): الْمَشَاكِلُ الَّتِي يَتْرُكُهَا خَلْفَهُ دَائِماً
--
reference: >al~a*iy yataDam~anu mazAyA barmajiy~apan wabaSariy~apan Eadiydapan tahdifu limuwAkabapi lt~aTaw~uri lHASili fiy lfaDA'i l<ilktruwniy watashiyli stifAdapi lqur~A'i min xadamAti lmawqiE
predicted: >al~a*iy yataDam~anu mazaAyaA baromajiy~apF wabaSariy~apF EadiydapF tahodifu limuwaAkabapi Alt~aTaw~uri AloHaASili fiy AlofaDaA'i Alo<iloktoruwniy watasohiyli AsotifaAdapi Aloqur~aA'i mino xadaAmaAti AlomawoqiEo
reference (untransliterated): أَلَّذِي يَتَضَمَّنُ مَزايا بَرمَجِيَّةَن وَبَصَرِيَّةَن عَدِيدَةَن تَهدِفُ لِمُواكَبَةِ لتَّطَوُّرِ لحاصِلِ فِي لفَضاءِ لإِلكترُونِي وَتَسهِيلِ ستِفادَةِ لقُرّاءِ مِن خَدَماتِ لمَوقِع
predicted (untransliterated): أَلَّذِي يَتَضَمَّنُ مَزَايَا بَرْمَجِيَّةً وَبَصَرِيَّةً عَدِيدَةً تَهْدِفُ لِمُوَاكَبَةِ التَّطَوُّرِ الْحَاصِلِ فِي الْفَضَاءِ الْإِلْكتْرُونِي وَتَسْهِيلِ اسْتِفَادَةِ الْقُرَّاءِ مِنْ خَدَامَاتِ الْمَوْقِعْ
--
reference: >alfikrapu wa<in badat jadiydapan EalY mujtamaEin yaEiy$u wAqiEan sayi}aan lA tu$aj~iEu EalY lD~aHik
predicted: >alofikorapu wa<inobadato jadiydapF EalaY mujotamaEK yaEiy$u waAqi Eano say~i}AF laA tu$aj~iEu EalaY AlD~aHiko
reference (untransliterated): أَلفِكرَةُ وَإِن بَدَت جَدِيدَةَن عَلى مُجتَمَعِن يَعِيشُ واقِعَن سَيِئََن لا تُشَجِّعُ عَلى لضَّحِك
predicted (untransliterated): أَلْفِكْرَةُ وَإِنْبَدَتْ جَدِيدَةً عَلَى مُجْتَمَعٍ يَعِيشُ وَاقِ عَنْ سَيِّئاً لَا تُشَجِّعُ عَلَى الضَّحِكْ
--
reference: mu$iyraan <ilY xidmapi lqur>Ani lkariymi wataEziyzi EalAqapi lmuslimiyna bihi
predicted: mu$iyrAF <ilaY xidomapi Aloquro|ni Alokariymi wataEoziyzi EalaAqapi Alomusolimiyna bihi
reference (untransliterated): مُشِيرََن إِلى خِدمَةِ لقُرأانِ لكَرِيمِ وَتَعزِيزِ عَلاقَةِ لمُسلِمِينَ بِهِ
predicted (untransliterated): مُشِيراً إِلَى خِدْمَةِ الْقُرْآنِ الْكَرِيمِ وَتَعْزِيزِ عَلَاقَةِ الْمُسْلِمِينَ بِهِ
--
reference: <in~ahu EindamA yakuwnu >aHadu lz~awjayni yastaxdimu >aHada >a$kAli lt~iknuwluwjyA >akvara mina l>Axar
predicted: <in~ahu EinodamaA yakuwnu >aHadu Alz~awojayoni yasotaxodimu >aHada >a$okaAli Alt~iykonuwluwjoyaA >akovara mina Alo|xaro
reference (untransliterated): إِنَّهُ عِندَما يَكُونُ أَحَدُ لزَّوجَينِ يَستَخدِمُ أَحَدَ أَشكالِ لتِّكنُولُوجيا أَكثَرَ مِنَ لأاخَر
predicted (untransliterated): إِنَّهُ عِنْدَمَا يَكُونُ أَحَدُ الزَّوْجَيْنِ يَسْتَخْدِمُ أَحَدَ أَشْكَالِ التِّيكْنُولُوجْيَا أَكْثَرَ مِنَ الْآخَرْ
--
reference: wa*alika biHuDuwri ra}yisi lhay}api
predicted: wa*alika biHuDuwri ra}iysi Alohayo>api
reference (untransliterated): وَذَلِكَ بِحُضُورِ رَئيِسِ لهَيئَةِ
predicted (untransliterated): وَذَلِكَ بِحُضُورِ رَئِيسِ الْهَيْأَةِ
--
reference: wa*alika fiy buTuwlapa ka>si lEAlami lil>andiyapi baEda nusxapin tAriyxiy~apin >alEAma lmADiya <intahat bitatwiyji bAyrin miyuwniyxa l>almAniy~a EalY HisAbi lr~ajA'i lmagribiy~i fiy >aw~ali ta>ah~ulin lifariyqin Earabiy~in <ilY nihA}iy~i lmusAbaqapi
predicted: wa*alika fiy buTuwlapi ka>osiy AloEaAlami lilo>anodiyapi baEoda nusoxapK taAriyxiy~apK >aloEaAma AlomaADiya <inotahato bitatowiyji bAyorinmoyuwnixa Alo>alomaAniy~a EalaY HisaAbi Alr~ajaA'i Alomagoribiy~ifiy >aw~ali ta>ah~ulK lifariyqKEarabiy~K <ilaY nihaA}iy~i AlomusaAbaqapi
reference (untransliterated): وَذَلِكَ فِي بُطُولَةَ كَأسِ لعالَمِ لِلأَندِيَةِ بَعدَ نُسخَةِن تارِيخِيَّةِن أَلعامَ لماضِيَ إِنتَهَت بِتَتوِيجِ بايرِن مِيُونِيخَ لأَلمانِيَّ عَلى حِسابِ لرَّجاءِ لمَغرِبِيِّ فِي أَوَّلِ تَأَهُّلِن لِفَرِيقِن عَرَبِيِّن إِلى نِهائِيِّ لمُسابَقَةِ
predicted (untransliterated): وَذَلِكَ فِي بُطُولَةِ كَأْسِي الْعَالَمِ لِلْأَنْدِيَةِ بَعْدَ نُسْخَةٍ تَارِيخِيَّةٍ أَلْعَامَ الْمَاضِيَ إِنْتَهَتْ بِتَتْوِيجِ بايْرِنمْيُونِخَ الْأَلْمَانِيَّ عَلَى حِسَابِ الرَّجَاءِ الْمَغْرِبِيِّفِي أَوَّلِ تَأَهُّلٍ لِفَرِيقٍعَرَبِيٍّ إِلَى نِهَائِيِّ الْمُسَابَقَةِ
--
reference: bal yajibu lbaHvu fiymA tumav~iluhu min <iDAfapin Haqiyqiy~apin lil<iqtiSAdi lmaSriy~i fiy majAlAti lt~awZiyf biAEtibAri >an~a mu$kilapa lbiTAlapi mina lmu$kilAti lr~a}iysiy~api fiy miSr
predicted: balo yajibu AlobaHovu fiymaA tumav~iluhu mino <iDaAfapK Haqiyqiy~apK lilo<iqotiSaAdi AlomaSoriy~i fiy majaAlaAti Alt~awoZiyfo biAEotibaAri >an~a mu$okilapa AlobiTaAlapi mina Alomu$okilaAti Alr~a}iysiy~api fiy miSori
reference (untransliterated): بَل يَجِبُ لبَحثُ فِيما تُمَثِّلُهُ مِن إِضافَةِن حَقِيقِيَّةِن لِلإِقتِصادِ لمَصرِيِّ فِي مَجالاتِ لتَّوظِيف بِاعتِبارِ أَنَّ مُشكِلَةَ لبِطالَةِ مِنَ لمُشكِلاتِ لرَّئِيسِيَّةِ فِي مِصر
predicted (untransliterated): بَلْ يَجِبُ الْبَحْثُ فِيمَا تُمَثِّلُهُ مِنْ إِضَافَةٍ حَقِيقِيَّةٍ لِلْإِقْتِصَادِ الْمَصْرِيِّ فِي مَجَالَاتِ التَّوْظِيفْ بِاعْتِبَارِ أَنَّ مُشْكِلَةَ الْبِطَالَةِ مِنَ الْمُشْكِلَاتِ الرَّئِيسِيَّةِ فِي مِصْرِ
--
reference: taHtaDinu qAEapu *A fiynyuw wasaTa bayruwta maEriDa lfan~i l<istivnA}iy~i
predicted: taHotaDinu qaAEapu *aAfiynoyw wasaTa bayoruwta maEoriDa Alofan~i Alo<isotivonaA}iy~i
reference (untransliterated): تَحتَضِنُ قاعَةُ ذا فِينيُو وَسَطَ بَيرُوتَ مَعرِضَ لفَنِّ لإِستِثنائِيِّ
predicted (untransliterated): تَحْتَضِنُ قَاعَةُ ذَافِينْيو وَسَطَ بَيْرُوتَ مَعْرِضَ الْفَنِّ الْإِسْتِثْنَائِيِّ
--
reference: tarbiyapu lHamAmi hiwAyapun wamihnapun libaEDi ln~As
predicted: tarobiy~apu AloHamaAmi hiwaAyapN wamihonapN libaEoDi Aln~aAs
reference (untransliterated): تَربِيَةُ لحَمامِ هِوايَةُن وَمِهنَةُن لِبَعضِ لنّاس
predicted (untransliterated): تَرْبِيَّةُ الْحَمَامِ هِوَايَةٌ وَمِهْنَةٌ لِبَعْضِ النَّاس
--
reference: tasEY $abakapu lt~awASuli l<ijtimAEiy~i lS~AEidapu <iylw <ilY munAfasapi $abakapi fysbuwk Eabra lt~axal~iy Eani l<iElAnAti wAlHifAZi EalY lxuSuwSiy~api waHimAyapi lbayAnAt
predicted: tasoEap $abakapu Alt~awaASuli Alo<ijotimaAEiy~i AlS~aAEidapu <iylw <ilaY munaAfasapi $abakapi fysobuwko Eabora Alt~axal~iy Eani Alo<iEolaAnaAti waAloHifaAZi EalaY AloxuSuwSiy~api waHimaAyapi AlobayaAnaAt
reference (untransliterated): تَسعى شَبَكَةُ لتَّواصُلِ لإِجتِماعِيِّ لصّاعِدَةُ إِيلو إِلى مُنافَسَةِ شَبَكَةِ فيسبُوك عَبرَ لتَّخَلِّي عَنِ لإِعلاناتِ والحِفاظِ عَلى لخُصُوصِيَّةِ وَحِمايَةِ لبَيانات
predicted (untransliterated): تَسْعَة شَبَكَةُ التَّوَاصُلِ الْإِجْتِمَاعِيِّ الصَّاعِدَةُ إِيلو إِلَى مُنَافَسَةِ شَبَكَةِ فيسْبُوكْ عَبْرَ التَّخَلِّي عَنِ الْإِعْلَانَاتِ وَالْحِفَاظِ عَلَى الْخُصُوصِيَّةِ وَحِمَايَةِ الْبَيَانَات
--
reference: jamEu lmu&ana~vi lsa~Alimi mivla fAzat <iHdY lTa~AlibAti fiy musAbaqapi lqirA'Ati lqur>Aniya~pi
predicted: jamoEu Alomu&an~avi Als~aAlimi mivola faAzato <iHodaY AlT~aAlibaAti fiy musaAbaqapi AloqiraA'aAti Aloquro|niy~api
reference (untransliterated): جَمعُ لمُؤَنَّثِ لسَّالِمِ مِثلَ فازَت إِحدى لطَّالِباتِ فِي مُسابَقَةِ لقِراءاتِ لقُرأانِيَّةِ
predicted (untransliterated): جَمْعُ الْمُؤَنَّثِ السَّالِمِ مِثْلَ فَازَتْ إِحْدَى الطَّالِبَاتِ فِي مُسَابَقَةِ الْقِرَاءَاتِ الْقُرْآنِيَّةِ
--
reference: Hat~Y l>amsi lqariyb kAna lkaviyru mina l>uwkrAniy~iyn yu$ak~ikuwna fiy ntimA'i tatAri $ibhi jaziyrapi lqarm
predicted: Hat~aY Alo>amosi Aloqariybo kaAna Alokaviyru mina Alo>uwkoraAniy~iyno yu$ak~ikuwna fiy AnotimaA'i tataAri $ibohi jaziyrapi Aloqaromo
reference (untransliterated): حَتّى لأَمسِ لقَرِيب كانَ لكَثِيرُ مِنَ لأُوكرانِيِّين يُشَكِّكُونَ فِي نتِماءِ تَتارِ شِبهِ جَزِيرَةِ لقَرم
predicted (untransliterated): حَتَّى الْأَمْسِ الْقَرِيبْ كَانَ الْكَثِيرُ مِنَ الْأُوكْرَانِيِّينْ يُشَكِّكُونَ فِي انْتِمَاءِ تَتَارِ شِبْهِ جَزِيرَةِ الْقَرْمْ
--
reference: Ha*~arati l>umamu lmut~aHidapu min >an~a lEAlama sayuwAjihu xilAla lEuquwdi lmuqbilapi tafAquma >azmapin muzdawijapin fiy lmiyAh wAlkahrabA'
predicted: Ha*~arapi Alo>umamu Alomut~aHidapu mino >an~a AloEaAlama sayuwaAjihu xilaAla AloEuquwdi Alomuqobilapi tafaAq~uma >azomapK muzodawyijapK fiy AlomiyaA waAlokahorabaA'o
reference (untransliterated): حَذَّرَتِ لأُمَمُ لمُتَّحِدَةُ مِن أَنَّ لعالَمَ سَيُواجِهُ خِلالَ لعُقُودِ لمُقبِلَةِ تَفاقُمَ أَزمَةِن مُزدَوِجَةِن فِي لمِياه والكَهرَباء
predicted (untransliterated): حَذَّرَةِ الْأُمَمُ الْمُتَّحِدَةُ مِنْ أَنَّ الْعَالَمَ سَيُوَاجِهُ خِلَالَ الْعُقُودِ الْمُقْبِلَةِ تَفَاقُّمَ أَزْمَةٍ مُزْدَويِجَةٍ فِي الْمِيَا وَالْكَهْرَبَاءْ
--
reference: HuDuwru baEDi lz~uEamA'i fiy >almasiyrapi ljumhuwriy~api bibAriys
predicted: HuDuwru baEoDi Alz~aEamaA'ifiy >alomasiyrapi Alojumohuwriy~api bibaArys
reference (untransliterated): حُضُورُ بَعضِ لزُّعَماءِ فِي أَلمَسِيرَةِ لجُمهُورِيَّةِ بِبارِيس
predicted (untransliterated): حُضُورُ بَعْضِ الزَّعَمَاءِفِي أَلْمَسِيرَةِ الْجُمْهُورِيَّةِ بِبَاريس
--
reference: Hayvu kAna lEarabu >w~ala man Earafa qiymatahA lEilAjiy~apa fiy lqarni lEA$iri qabla lmiylAd fiy mamlakapi saba>
predicted: Hayovu kaAna AloEarabu >aw~ala mano Earafa qiymatahaA AloEilaAjiy~apa fiy Aloqaroni AloEaA$iri qabola AlomiylaAd fiy mamolakapi saba>o
reference (untransliterated): حَيثُ كانَ لعَرَبُ أوَّلَ مَن عَرَفَ قِيمَتَها لعِلاجِيَّةَ فِي لقَرنِ لعاشِرِ قَبلَ لمِيلاد فِي مَملَكَةِ سَبَأ
predicted (untransliterated): حَيْثُ كَانَ الْعَرَبُ أَوَّلَ مَنْ عَرَفَ قِيمَتَهَا الْعِلَاجِيَّةَ فِي الْقَرْنِ الْعَاشِرِ قَبْلَ الْمِيلَاد فِي مَمْلَكَةِ سَبَأْ
--
reference: daxalati lt~iknuwluwjyA fiy kul~i baytin wa>usrapin wa>aSbaHat tu$ak~ilu ljuz'a lkabiyra min HayAtinA
predicted: daxalati Alt~ikonuwluwjoyaA fiy kul~i bayotK wa>usorapK wa>aSobaHaAtlotu$ak~ilu Alojuzo'a Alokabiyra mino HayaAtina
reference (untransliterated): دَخَلَتِ لتِّكنُولُوجيا فِي كُلِّ بَيتِن وَأُسرَةِن وَأَصبَحَت تُشَكِّلُ لجُزءَ لكَبِيرَ مِن حَياتِنا
predicted (untransliterated): دَخَلَتِ التِّكْنُولُوجْيَا فِي كُلِّ بَيْتٍ وَأُسْرَةٍ وَأَصْبَحَاتلْتُشَكِّلُ الْجُزْءَ الْكَبِيرَ مِنْ حَيَاتِنَ
--
reference: duwna taHmiyli ljismi juhdan kabiyran fiy lbidAyapi qad yatasaba~bu fiy nufuwri l$a~xSi mina l<istimrAr
predicted: duwna taHomiyli Alojisomi juhodAF kabiyrAF fiy AlobidaAyapi qado yatasab~abu fiy nufuwri Al$~axoSi mina Al<isotimoraAro
reference (untransliterated): دُونَ تَحمِيلِ لجِسمِ جُهدَن كَبِيرَن فِي لبِدايَةِ قَد يَتَسَبَّبُ فِي نُفُورِ لشَّخصِ مِنَ لإِستِمرار
predicted (untransliterated): دُونَ تَحْمِيلِ الْجِسْمِ جُهْداً كَبِيراً فِي الْبِدَايَةِ قَدْ يَتَسَبَّبُ فِي نُفُورِ الشَّخْصِ مِنَ الإِسْتِمْرَارْ
--
reference: ragma ln~izAEi ld~Amiy >al~a*iy yaESifu biAlbilAd mun*u val>avi sanawAt
predicted: ragoma Aln~izaAEi Ald~aAmiy >al~a*iy yaEoSifu biAlobilAd muno*u valAvi sanawAt
reference (untransliterated): رَغمَ لنِّزاعِ لدّامِي أَلَّذِي يَعصِفُ بِالبِلاد مُنذُ ثَلأَثِ سَنَوات
predicted (untransliterated): رَغْمَ النِّزَاعِ الدَّامِي أَلَّذِي يَعْصِفُ بِالْبِلاد مُنْذُ ثَلاثِ سَنَوات
--
reference: rafaDa majlisu l>amni ld~awliy~u ma$ruwEa lqarAri lfilisTiyniy~i lr~Amiy <ilY <inhA'i l<iHtilAli l<isrA}iyliy~i fiy EAmayn
predicted: rafaDa majolisu Alo>amoni Ald~awoliy~u ma$oruwEa AloqaraAri AlofilisoTiyniy~i Alr~aAmi <ilaY <inohaA'i Alo<iHotilaAli Alo<isoraA}iyliy~i fiy EaAmayno
reference (untransliterated): رَفَضَ مَجلِسُ لأَمنِ لدَّولِيُّ مَشرُوعَ لقَرارِ لفِلِسطِينِيِّ لرّامِي إِلى إِنهاءِ لإِحتِلالِ لإِسرائِيلِيِّ فِي عامَين
predicted (untransliterated): رَفَضَ مَجْلِسُ الْأَمْنِ الدَّوْلِيُّ مَشْرُوعَ الْقَرَارِ الْفِلِسْطِينِيِّ الرَّامِ إِلَى إِنْهَاءِ الْإِحْتِلَالِ الْإِسْرَائِيلِيِّ فِي عَامَينْ
--
reference: ramzu ld~awlapi lt~urkiy~api lEilmAniy~api al~atiy ta>as~asat Eaqiba nhiyAri ld~awlapi lEuvmAniy~api
predicted: ramozu Ald~awolapi Alt~urokiy~api AloEilomaAniy~api Al~atiy ta>as~asato EaqibaAF hiyaAri Ald~awolapi AloEuvomaAniy~api
reference (untransliterated): رَمزُ لدَّولَةِ لتُّركِيَّةِ لعِلمانِيَّةِ َلَّتِي تَأَسَّسَت عَقِبَ نهِيارِ لدَّولَةِ لعُثمانِيَّةِ
predicted (untransliterated): رَمْزُ الدَّوْلَةِ التُّرْكِيَّةِ الْعِلْمَانِيَّةِ الَّتِي تَأَسَّسَتْ عَقِبَاً هِيَارِ الدَّوْلَةِ الْعُثْمَانِيَّةِ
--
reference: $Araka mawqiEu >aljaziyrapi litaEal~umi lEarabiy~api fiy lmu&tamari ld~awliy~i lv~Aniy lil~ugapi lEarabiy~api >al~a*iy naZ~amathu jAmiEapu mawlAnA mAlik <ibrAhiym >al<islAmiy~apu lHukuwmiyapu bimadiynapi mAlAnq biAlt~aEAwuni maEa jAmiEapi dAri ls~alAm bimadiynapi kuwntuwr fiy >anduwniysyA
predicted: $aAraka mawoqiEu >alojaziyrapi litaEal~umi AloEarabiy~api fiy Alomu&otamari Ald~awoliy~i Alv~aAniy lill~ugapi AloEarabiy~api >al~a*iy naZ~amatohu jaAmiEapu mawolaAnaA maAlik <iboraAhiymo >alo<isolaAmiy~apu AloHukuwmiy~apu bimadiynapi maA laAnoqo biAlt~aEaAwuni maEa jaAmiEapi daAri Als~alaAmo bimadiynapi kuwnotuwro fiy >anoduwniysoyaA
reference (untransliterated): شارَكَ مَوقِعُ أَلجَزِيرَةِ لِتَعَلُّمِ لعَرَبِيَّةِ فِي لمُؤتَمَرِ لدَّولِيِّ لثّانِي لِلُّغَةِ لعَرَبِيَّةِ أَلَّذِي نَظَّمَتهُ جامِعَةُ مَولانا مالِك إِبراهِيم أَلإِسلامِيَّةُ لحُكُومِيَةُ بِمَدِينَةِ مالانق بِالتَّعاوُنِ مَعَ جامِعَةِ دارِ لسَّلام بِمَدِينَةِ كُونتُور فِي أَندُونِيسيا
predicted (untransliterated): شَارَكَ مَوْقِعُ أَلْجَزِيرَةِ لِتَعَلُّمِ الْعَرَبِيَّةِ فِي الْمُؤْتَمَرِ الدَّوْلِيِّ الثَّانِي لِللُّغَةِ الْعَرَبِيَّةِ أَلَّذِي نَظَّمَتْهُ جَامِعَةُ مَوْلَانَا مَالِك إِبْرَاهِيمْ أَلْإِسْلَامِيَّةُ الْحُكُومِيَّةُ بِمَدِينَةِ مَا لَانْقْ بِالتَّعَاوُنِ مَعَ جَامِعَةِ دَارِ السَّلَامْ بِمَدِينَةِ كُونْتُورْ فِي أَنْدُونِيسْيَا
--
reference: $araEa l<it~iHAdu lt~uwnusiy~u lilfuruwsiy~api fiy tanfiy* xuT~apin tarnuw <ilY lmuDiy~i biha*ihi lr~iyADapi naHwa buluwgi lEAlamiy~api
predicted: $aAraEa Alo<it~iHaAdu Alt~uwnusiy~u lilofuruwsiy~api fiy tanofiy*o xuT~apK taronuwA <ilaY AlomuDiy~i biha*ihi Alr~iy~aADapi naHowa buluwgi AloEaAlamiy~api
reference (untransliterated): شَرَعَ لإِتِّحادُ لتُّونُسِيُّ لِلفُرُوسِيَّةِ فِي تَنفِيذ خُطَّةِن تَرنُو إِلى لمُضِيِّ بِهَذِهِ لرِّياضَةِ نَحوَ بُلُوغِ لعالَمِيَّةِ
predicted (untransliterated): شَارَعَ الْإِتِّحَادُ التُّونُسِيُّ لِلْفُرُوسِيَّةِ فِي تَنْفِيذْ خُطَّةٍ تَرْنُوا إِلَى الْمُضِيِّ بِهَذِهِ الرِّيَّاضَةِ نَحْوَ بُلُوغِ الْعَالَمِيَّةِ
--
reference: $ahida EAmu >alfayni wa>arbaEapa Ea$rapa Eid~apa <injAzAtin Tib~iy~apin
predicted: $ahida EaAmu >alfayni wa>arobaEapa Ea$orapa Eid~apa <inojaAzaAtK Tib~iy~apK
reference (untransliterated): شَهِدَ عامُ أَلفَينِ وَأَربَعَةَ عَشرَةَ عِدَّةَ إِنجازاتِن طِبِّيَّةِن
predicted (untransliterated): شَهِدَ عَامُ أَلفَينِ وَأَرْبَعَةَ عَشْرَةَ عِدَّةَ إِنْجَازَاتٍ طِبِّيَّةٍ
--
reference: EAda <irtifAEu >asEAri l>dwiyapi wa$uH~u lmunqi*i lilHayApi minhA liyuTil~a bira>sihi fiy ls~uwdAni min jadiydin
predicted: EaAda <irotifaAEu >asoEaAri Alo>adowiyapi wa$uH~u Alomunoqi*i liloHayaAti minohaA liyuTil~a bira>osihi fiy Als~uwdaAni mino jadiydK
reference (untransliterated): عادَ إِرتِفاعُ أَسعارِ لأدوِيَةِ وَشُحُّ لمُنقِذِ لِلحَياةِ مِنها لِيُطِلَّ بِرَأسِهِ فِي لسُّودانِ مِن جَدِيدِن
predicted (untransliterated): عَادَ إِرْتِفَاعُ أَسْعَارِ الْأَدْوِيَةِ وَشُحُّ الْمُنْقِذِ لِلْحَيَاتِ مِنْهَا لِيُطِلَّ بِرَأْسِهِ فِي السُّودَانِ مِنْ جَدِيدٍ
--
reference: EalY EtibArihA tusAEidu EalY tawsiyEi madAriki l>aTfAl watajEalu minhum >unAsan muvaq~afiyna mustaqbalan wamuwAkibiyna liEaSri tiknuwluwjyA lmaEluwmAt
predicted: EalaY AEotibaArihaA tusaAEidu EalaY tawosiyEi ma*ariki Alo>aTofaAl watajoEalu minohumo >unaAsAF muvaq~afiyna musotaqobalAF wamuwaAkibiyna liEaSori Alt~ikonuwluwjoyaA AlomaEoluwmaAt
reference (untransliterated): عَلى عتِبارِها تُساعِدُ عَلى تَوسِيعِ مَدارِكِ لأَطفال وَتَجعَلُ مِنهُم أُناسَن مُثَقَّفِينَ مُستَقبَلَن وَمُواكِبِينَ لِعَصرِ تِكنُولُوجيا لمَعلُومات
predicted (untransliterated): عَلَى اعْتِبَارِهَا تُسَاعِدُ عَلَى تَوْسِيعِ مَذَرِكِ الْأَطْفَال وَتَجْعَلُ مِنْهُمْ أُنَاساً مُثَقَّفِينَ مُسْتَقْبَلاً وَمُوَاكِبِينَ لِعَصْرِ التِّكْنُولُوجْيَا الْمَعْلُومَات
--
reference: wa*alika EalY xilAfi nuZarA}ihi ls~Abiqiyn
predicted: wa*alika EalaY xilaAfi nuZaraA}ihi Als~aAbiqiyno
reference (untransliterated): وَذَلِكَ عَلى خِلافِ نُظَرائِهِ لسّابِقِين
predicted (untransliterated): وَذَلِكَ عَلَى خِلَافِ نُظَرَائِهِ السَّابِقِينْ
--
reference: fataHat >akAdiymiy~apu lmuwsiyqY lEarabiy~api rasmiy~an yawma ls~abt >abwAbahA fiy bruwksil biHuDuwri majmuwEapin mina lwuzarA' warijAli lfan~i lbaljiykiy~iyna wAlEarab
predicted: fataHato >akaAdiymiy~apu AlomuwsiyqaY AloEarabiy~api rasomiy~AF yawoma Als~abot >abowaAbahaA fiy boruwkosil biHuDuwri majomuwEapK mina AlowuzaraYA warijaAli Alofan~i Alobalojiykiy~iyna waAloEarabo
reference (untransliterated): فَتَحَت أَكادِيمِيَّةُ لمُوسِيقى لعَرَبِيَّةِ رَسمِيَّن يَومَ لسَّبت أَبوابَها فِي برُوكسِل بِحُضُورِ مَجمُوعَةِن مِنَ لوُزَراء وَرِجالِ لفَنِّ لبَلجِيكِيِّينَ والعَرَب
predicted (untransliterated): فَتَحَتْ أَكَادِيمِيَّةُ الْمُوسِيقَى الْعَرَبِيَّةِ رَسْمِيّاً يَوْمَ السَّبْت أَبْوَابَهَا فِي بْرُوكْسِل بِحُضُورِ مَجْمُوعَةٍ مِنَ الْوُزَرَىا وَرِجَالِ الْفَنِّ الْبَلْجِيكِيِّينَ وَالْعَرَبْ
--
reference: fataHZY bitaEal~umin yamHuw >um~iy~atahA wayuDiy'u lahA Tariyqa lmaErifapi wAlt~iknuwluwjyA
predicted: fataHoZaY bitaEal~umK yamoHu >um~iy~atahaA wayuDiy'u lahaA Tariyqa AlomaEorifapi waAlt~iykonuwluwjoyaA
reference (untransliterated): فَتَحظى بِتَعَلُّمِن يَمحُو أُمِّيَّتَها وَيُضِيءُ لَها طَرِيقَ لمَعرِفَةِ والتِّكنُولُوجيا
predicted (untransliterated): فَتَحْظَى بِتَعَلُّمٍ يَمْحُ أُمِّيَّتَهَا وَيُضِيءُ لَهَا طَرِيقَ الْمَعْرِفَةِ وَالتِّيكْنُولُوجْيَا
--
reference: faha*A lmanzilu lmutawADiE >aSbaHa maHaj~aan liEadadin kabiyrin mina ln~isA'i lmariyDAti biAls~araTAn
predicted: faha*aA Alomanozilu AlomutawaADiEi >aSobaHa maHaj~AF liEadadK kabiyrK mina Aln~isaA'i AlomariyDaAti biAls~araTaAno
reference (untransliterated): فَهَذا لمَنزِلُ لمُتَواضِع أَصبَحَ مَحَجََّن لِعَدَدِن كَبِيرِن مِنَ لنِّساءِ لمَرِيضاتِ بِالسَّرَطان
predicted (untransliterated): فَهَذَا الْمَنْزِلُ الْمُتَوَاضِعِ أَصْبَحَ مَحَجّاً لِعَدَدٍ كَبِيرٍ مِنَ النِّسَاءِ الْمَرِيضَاتِ بِالسَّرَطَانْ
--
reference: Hadava *alika fiy Hay yaEquwba lmanSuwr l$~aEbiy~i
predicted: Hadava *alika fiy Hay yaEoquwba AlomanoSuwro >al$~aEobiy~i
reference (untransliterated): حَدَثَ ذَلِكَ فِي حَي يَعقُوبَ لمَنصُور لشَّعبِيِّ
predicted (untransliterated): حَدَثَ ذَلِكَ فِي حَي يَعْقُوبَ الْمَنْصُورْ أَلشَّعْبِيِّ
--
reference: fiy Hiyni kAna lmarkazu l>aw~alu fiy lwavbi lEAliy min naSiybi lkuruwAtiy~api >AnA siymiyt$
predicted: fiy Hiyni kaAna Alomarokazu Alo>aw~alu fiy Alowavobi AloEaAli mino naSiybi AlokuruwaAtiy~api |naA siymito$
reference (untransliterated): فِي حِينِ كانَ لمَركَزُ لأَوَّلُ فِي لوَثبِ لعالِي مِن نَصِيبِ لكُرُواتِيَّةِ أانا سِيمِيتش
predicted (untransliterated): فِي حِينِ كَانَ الْمَرْكَزُ الْأَوَّلُ فِي الْوَثْبِ الْعَالِ مِنْ نَصِيبِ الْكُرُوَاتِيَّةِ آنَا سِيمِتْش
--
reference: qAla bAHivuwna <in~a riyAHan >aqwY mina lmuEtAd xaf~afat min HarArapi saTHi lmuHiyTi lhAdiy hiya sababu lt~abATu}i lmu&aq~at fiy rtifAEi darajapi HarArapi l>arD mun*u bidAyapi lqarni lHAdiy wAlEi$riyn
predicted: qaAla baAHivuwna <in~a riyaAHAF >aqowaY mina AlomuEotaAd xaf~afato mino HaraArapi saToHi AlomuHiyTi AlohaAdiy hiya sababu Alt~abaATu&i Alomu&aq~aTi fiy ArotifaAEi darajapi HaraArapi Alo>aroD muno*u bidaAyapi Aloqaroni AloHaAdiy waAloEi$oriyno
reference (untransliterated): قالَ باحِثُونَ إِنَّ رِياحَن أَقوى مِنَ لمُعتاد خَفَّفَت مِن حَرارَةِ سَطحِ لمُحِيطِ لهادِي هِيَ سَبَبُ لتَّباطُئِ لمُؤَقَّت فِي رتِفاعِ دَرَجَةِ حَرارَةِ لأَرض مُنذُ بِدايَةِ لقَرنِ لحادِي والعِشرِين
predicted (untransliterated): قَالَ بَاحِثُونَ إِنَّ رِيَاحاً أَقْوَى مِنَ الْمُعْتَاد خَفَّفَتْ مِنْ حَرَارَةِ سَطْحِ الْمُحِيطِ الْهَادِي هِيَ سَبَبُ التَّبَاطُؤِ الْمُؤَقَّطِ فِي ارْتِفَاعِ دَرَجَةِ حَرَارَةِ الْأَرْض مُنْذُ بِدَايَةِ الْقَرْنِ الْحَادِي وَالْعِشْرِينْ
--
reference: qabla >an yuslima liyudAfiEa Ean diynih muHib~aan wamuHtariman li>aSlihi wamADiyh
predicted: qabola >ano yusolima liyudaAfiEa Eano diyni muHib~AF wamuHotarimAF li>aSolihi wamaADiyh
reference (untransliterated): قَبلَ أَن يُسلِمَ لِيُدافِعَ عَن دِينِه مُحِبََّن وَمُحتَرِمَن لِأَصلِهِ وَماضِيه
predicted (untransliterated): قَبْلَ أَنْ يُسْلِمَ لِيُدَافِعَ عَنْ دِينِ مُحِبّاً وَمُحْتَرِماً لِأَصْلِهِ وَمَاضِيه
--
reference: kamA tam~a taHsiynu wAjihAti lt~anaq~ul wAxtiyAri wasA}ili ln~aqli lmunAsibapi bi$aklin kabiyr
predicted: kamaA tam~a taHosiynu waAjihaAti Alt~anaq~ulo waAxotiyaAri wasaA}ili Aln~aqoli AlomunaAsibapi bi$akolK kabiyro
reference (untransliterated): كَما تَمَّ تَحسِينُ واجِهاتِ لتَّنَقُّل واختِيارِ وَسائِلِ لنَّقلِ لمُناسِبَةِ بِشَكلِن كَبِير
predicted (untransliterated): كَمَا تَمَّ تَحْسِينُ وَاجِهَاتِ التَّنَقُّلْ وَاخْتِيَارِ وَسَائِلِ النَّقْلِ الْمُنَاسِبَةِ بِشَكْلٍ كَبِيرْ
--
reference: kamA tuwuf~iyati lr~iwA}iy~apu lbArizapu wAl>ustA*apu ljAmiEiy~apu lmiSriy~apu raDwY EA$uwr Ean vamAniy wasit~iyna EAman
predicted: kamaA tuwuf~iyapi Alr~iwaA}iy~apu AlobaArizapu waAlo>usotaA*apu Alj~aAmiEiy~apu AlomiSoriy~apu raDowaY EaA$uwro Eano vamaAniy wasit~iyna EaAmAF
reference (untransliterated): كَما تُوُفِّيَتِ لرِّوائِيَّةُ لبارِزَةُ والأُستاذَةُ لجامِعِيَّةُ لمِصرِيَّةُ رَضوى عاشُور عَن ثَمانِي وَسِتِّينَ عامَن
predicted (untransliterated): كَمَا تُوُفِّيَةِ الرِّوَائِيَّةُ الْبَارِزَةُ وَالْأُسْتَاذَةُ الجَّامِعِيَّةُ الْمِصْرِيَّةُ رَضْوَى عَاشُورْ عَنْ ثَمَانِي وَسِتِّينَ عَاماً
--
reference: kamA $Arakat TAlibAtun min madArisa filasTiyniy~apin >alfan~Anapa lt~urkiy~apa fiy Eamali lawHAt
predicted: kamaA $aArakato TaAlibaAtN mino madaArisa fiylasoTiydiy~apK >alofan~aAnapa Alt~urokiy~apa fiy Eamali lawoHaAt
reference (untransliterated): كَما شارَكَت طالِباتُن مِن مَدارِسَ فِلَسطِينِيَّةِن أَلفَنّانَةَ لتُّركِيَّةَ فِي عَمَلِ لَوحات
predicted (untransliterated): كَمَا شَارَكَتْ طَالِبَاتٌ مِنْ مَدَارِسَ فِيلَسْطِيدِيَّةٍ أَلْفَنَّانَةَ التُّرْكِيَّةَ فِي عَمَلِ لَوْحَات
--
reference: lAmasa mu*an~abun yuTlaqu Ealayhi <ismu sAydiyng sbriyng kawkaba lmir~iyxi Einda muruwrihi bimuHA*Atih
predicted: laAmasa mu*an~abN yuTolaqu Ealayohi <isomu saAyodynosoboriynogo kawokaba Alomar~iyxi Einoda muruwrihi bimuHaA*aAti
reference (untransliterated): لامَسَ مُذَنَّبُن يُطلَقُ عَلَيهِ إِسمُ سايدِينغ سبرِينغ كَوكَبَ لمِرِّيخِ عِندَ مُرُورِهِ بِمُحاذاتِه
predicted (untransliterated): لَامَسَ مُذَنَّبٌ يُطْلَقُ عَلَيْهِ إِسْمُ سَايْدينْسْبْرِينْغْ كَوْكَبَ الْمَرِّيخِ عِنْدَ مُرُورِهِ بِمُحَاذَاتِ
--
reference: laqad sAhamati lt~iknuluwjyA fiy taqliyli ln~izAEAti l>usariy~api wa>aETat likul~i fardin nawEan mina l<istiqlAliy~api
predicted: laqado saAhamapi Alt~iykonuwluwjoyaA fiy taqoliyli Aln~izaAEaAti Alo>usariy~api wa>aEoTaTo likul~i farodK nawoEAF mina Alo<isotiqolaAliy~api
reference (untransliterated): لَقَد ساهَمَتِ لتِّكنُلُوجيا فِي تَقلِيلِ لنِّزاعاتِ لأُسَرِيَّةِ وَأَعطَت لِكُلِّ فَردِن نَوعَن مِنَ لإِستِقلالِيَّةِ
predicted (untransliterated): لَقَدْ سَاهَمَةِ التِّيكْنُولُوجْيَا فِي تَقْلِيلِ النِّزَاعَاتِ الْأُسَرِيَّةِ وَأَعْطَطْ لِكُلِّ فَرْدٍ نَوْعاً مِنَ الْإِسْتِقْلَالِيَّةِ
--
reference: lakin~a maSdaran fiy lwafdi qAl <in~a ls~iEra sayanxafiDu baEda nxifADi >asEAri ln~afTi fiy lEAlam
predicted: lakin~a maSodarAF fiy Alowafodi qaAl <in~a Als~iEoara sayanoxafiDu baEoda AnoxifaADi >asoEaAri Aln~afoTi fiy AloEaAlamo
reference (untransliterated): لَكِنَّ مَصدَرَن فِي لوَفدِ قال إِنَّ لسِّعرَ سَيَنخَفِضُ بَعدَ نخِفاضِ أَسعارِ لنَّفطِ فِي لعالَم
predicted (untransliterated): لَكِنَّ مَصْدَراً فِي الْوَفْدِ قَال إِنَّ السِّعَْرَ سَيَنْخَفِضُ بَعْدَ انْخِفَاضِ أَسْعَارِ النَّفْطِ فِي الْعَالَمْ
--
reference: lam yamnaE DaEfu mawAridi lt~amwiyl wArtifAEu kulfapi lmu$ArakAti ld~awliy~api riyADapa lfuruwsiy~api fiy tuwnusa min >an tastaqTiba lmi}At min Eu$~AqihA fiy baladin yakAdu l<ihtimAmu fiyhi yaqtaSir EalY riyADAtin $aEbiy~apin muEay~anapin
predicted: lamo yamonaEoDaEaofu mawaAridi Alt~amowiylo waArotifaAEu kulofapi Alomu$aArakaAti Ald~awoliy~api riyaADapa Alofuruwsiy~api fiy tuwnusa mino >ano tasotaqoTiba Almi}At mino Eu$~aAqihaA fiy baladK yakaAdu Al<ihotimaAmu fiy hiyaqotaSir EalaY riy~aADaAtK $aEobiy~apK muEay~inapK
reference (untransliterated): لَم يَمنَع ضَعفُ مَوارِدِ لتَّموِيل وارتِفاعُ كُلفَةِ لمُشارَكاتِ لدَّولِيَّةِ رِياضَةَ لفُرُوسِيَّةِ فِي تُونُسَ مِن أَن تَستَقطِبَ لمِئات مِن عُشّاقِها فِي بَلَدِن يَكادُ لإِهتِمامُ فِيهِ يَقتَصِر عَلى رِياضاتِن شَعبِيَّةِن مُعَيَّنَةِن
predicted (untransliterated): لَمْ يَمْنَعْضَعَْفُ مَوَارِدِ التَّمْوِيلْ وَارْتِفَاعُ كُلْفَةِ الْمُشَارَكَاتِ الدَّوْلِيَّةِ رِيَاضَةَ الْفُرُوسِيَّةِ فِي تُونُسَ مِنْ أَنْ تَسْتَقْطِبَ المِئات مِنْ عُشَّاقِهَا فِي بَلَدٍ يَكَادُ الإِهْتِمَامُ فِي هِيَقْتَصِر عَلَى رِيَّاضَاتٍ شَعْبِيَّةٍ مُعَيِّنَةٍ
--
reference: liyaDaEA bi*alika Hadaan lilEadiydi mina lt~aqAriyr >al~atiy >ak~adat <imkAniy~apa raHiyli ll~AEibi lmu$Agibi qariybaan
predicted: liyaDaEaAbi *alika Had~AF liloEadiydi mina Alt~aqaAriyro >al~atiy >ak~adat <imokaAniy~apa raHiyli All~aAEibi Alomu$aAgibi qariybAF
reference (untransliterated): لِيَضَعا بِذَلِكَ حَدََن لِلعَدِيدِ مِنَ لتَّقارِير أَلَّتِي أَكَّدَت إِمكانِيَّةَ رَحِيلِ للّاعِبِ لمُشاغِبِ قَرِيبََن
predicted (untransliterated): لِيَضَعَابِ ذَلِكَ حَدّاً لِلْعَدِيدِ مِنَ التَّقَارِيرْ أَلَّتِي أَكَّدَت إِمْكَانِيَّةَ رَحِيلِ اللَّاعِبِ الْمُشَاغِبِ قَرِيباً
--
reference: muDiyfan nuHAwilu xalqa furaSi Eamalin bi>aydiynA
predicted: muDiyfAF nuHaAwilu xaloqa furaSi EamalK bi>ayodiyna
reference (untransliterated): مُضِيفَن نُحاوِلُ خَلقَ فُرَصِ عَمَلِن بِأَيدِينا
predicted (untransliterated): مُضِيفاً نُحَاوِلُ خَلْقَ فُرَصِ عَمَلٍ بِأَيْدِينَ
--
reference: wa*alika muqAranapan maEa lmaHASiyli lz~irAEiy~api l>uxrY
predicted: wa*alika muqaAranapF maEa AlomaHaASiyli Alz~iraAEiy~api Alo>uxoraY
reference (untransliterated): وَذَلِكَ مُقارَنَةَن مَعَ لمَحاصِيلِ لزِّراعِيَّةِ لأُخرى
predicted (untransliterated): وَذَلِكَ مُقَارَنَةً مَعَ الْمَحَاصِيلِ الزِّرَاعِيَّةِ الْأُخْرَى
--
reference: mulqiyan lD~aw'a EalY qaDiy~api lfitnapi lT~A}ifiy~api fiy lmujtamaEi lmiSriy~i bi>usluwbin basiyTin min xilAli EalAqAti l>aTfAl fiy lmadrasapi bizamiylihimu lmasiyHiy~i
predicted: muloqiyani AlD~awo'a EalaY qadiy~api Alofitonapi AlT~aA}ifiy~api fiy AlomujotamaEi AlomiSoriy~i bi>usoluwbK basiyTK mino xilaAli EalaAqaAti Alo>aTofaAlo fiy Alomadorasapi bizamiylihimu AlomasiyHiy~i
reference (untransliterated): مُلقِيَن لضَّوءَ عَلى قَضِيَّةِ لفِتنَةِ لطّائِفِيَّةِ فِي لمُجتَمَعِ لمِصرِيِّ بِأُسلُوبِن بَسِيطِن مِن خِلالِ عَلاقاتِ لأَطفال فِي لمَدرَسَةِ بِزَمِيلِهِمُ لمَسِيحِيِّ
predicted (untransliterated): مُلْقِيَنِ الضَّوْءَ عَلَى قَدِيَّةِ الْفِتْنَةِ الطَّائِفِيَّةِ فِي الْمُجْتَمَعِ الْمِصْرِيِّ بِأُسْلُوبٍ بَسِيطٍ مِنْ خِلَالِ عَلَاقَاتِ الْأَطْفَالْ فِي الْمَدْرَسَةِ بِزَمِيلِهِمُ الْمَسِيحِيِّ
--
reference: mim~A yadEamu natA}ija dirAsAtin sAbiqapin tuHa*~iru min maxATiri l<ifrATi fiy stiEmAli ljaw~Al
predicted: mim~aA yadoEamu nataA}ija diraAsaAtK saAbiqapK tuHa*~iru mino maxaATiri Alo<iforaATi fiy AsotiEomaAli Alj~aw~aAl
reference (untransliterated): مِمّا يَدعَمُ نَتائِجَ دِراساتِن سابِقَةِن تُحَذِّرُ مِن مَخاطِرِ لإِفراطِ فِي ستِعمالِ لجَوّال
predicted (untransliterated): مِمَّا يَدْعَمُ نَتَائِجَ دِرَاسَاتٍ سَابِقَةٍ تُحَذِّرُ مِنْ مَخَاطِرِ الْإِفْرَاطِ فِي اسْتِعْمَالِ الجَّوَّال
--
reference: min baynihA >al<istiqrAru wanawEiy~apu lr~iEAyapi lS~iH~iy~api wAlv~aqAfapi wAlbiy}api wAlt~aEliymi wAlbinyapi lt~aHtiy~api
predicted: mino bayonihaA >alo<isotiqoraAru wanawoEiy~apu Alr~iEaAyapi AlS~iH~iy~api waAlv~aqaAfapi waAlobiy}api waAlt~aEoliymi waAlobinoyapi Alt~aHotiy~api
reference (untransliterated): مِن بَينِها أَلإِستِقرارُ وَنَوعِيَّةُ لرِّعايَةِ لصِّحِّيَّةِ والثَّقافَةِ والبِيئَةِ والتَّعلِيمِ والبِنيَةِ لتَّحتِيَّةِ
predicted (untransliterated): مِنْ بَيْنِهَا أَلْإِسْتِقْرَارُ وَنَوْعِيَّةُ الرِّعَايَةِ الصِّحِّيَّةِ وَالثَّقَافَةِ وَالْبِيئَةِ وَالتَّعْلِيمِ وَالْبِنْيَةِ التَّحْتِيَّةِ
--
reference: minhA >aqmi$apun wa>adawAtun maEdaniy~apun waxa$abiy~apun waqinAnun blAstiykiy~apun wazujAjiy~apun wa>awrAqu SuHuf
predicted: minohaA >aqomi$apN wa>adawaAtN maEodaniy~apN waxa$abiy~apN waqinAnN bolaAsotiykiy~apN wazujaAjiy~atN wa>aworaAqu SuHafo
reference (untransliterated): مِنها أَقمِشَةُن وَأَدَواتُن مَعدَنِيَّةُن وَخَشَبِيَّةُن وَقِنانُن بلاستِيكِيَّةُن وَزُجاجِيَّةُن وَأَوراقُ صُحُف
predicted (untransliterated): مِنْهَا أَقْمِشَةٌ وَأَدَوَاتٌ مَعْدَنِيَّةٌ وَخَشَبِيَّةٌ وَقِنانٌ بْلَاسْتِيكِيَّةٌ وَزُجَاجِيَّتٌ وَأَوْرَاقُ صُحَفْ
--
reference: hal lilS~iyAmi ta>viyrun EalY Eamali lmuslimiyna fiy l$~arikAti bi>uwruwb~A
predicted: hal~i AlS~iyaAmi ta>oviyrN EalaY Eamali Alomusolimiyna fiy Al$~arikaAti bi>uwruwb~aA
reference (untransliterated): هَل لِلصِّيامِ تَأثِيرُن عَلى عَمَلِ لمُسلِمِينَ فِي لشَّرِكاتِ بِأُورُوبّا
predicted (untransliterated): هَلِّ الصِّيَامِ تَأْثِيرٌ عَلَى عَمَلِ الْمُسْلِمِينَ فِي الشَّرِكَاتِ بِأُورُوبَّا
--
reference: hunAka fikrapun TuriHat bAdi}a l>amr biEaqdi qim~apin >uwruwbiy~apin fiy sarayiyfuw biha*ihi lmunAsabapi
predicted: hunaAka fikorapN TuriHato baAdi >alo>amor biEaqoDi qim~apK >uwruwbiy~apK fiy sarayiyfuw biha*ihi AlomunaAsabapi
reference (untransliterated): هُناكَ فِكرَةُن طُرِحَت بادِئَ لأَمر بِعَقدِ قِمَّةِن أُورُوبِيَّةِن فِي سَرَيِيفُو بِهَذِهِ لمُناسَبَةِ
predicted (untransliterated): هُنَاكَ فِكْرَةٌ طُرِحَتْ بَادِ أَلْأَمْر بِعَقْضِ قِمَّةٍ أُورُوبِيَّةٍ فِي سَرَيِيفُو بِهَذِهِ الْمُنَاسَبَةِ
--
reference: wa yumkinu >an tuHSada lv~imAr EalY madY fatrapin zamaniy~apin Tawiylapin
predicted: wayumokinu >ano tuHoSada Alv~imaAr EalaY madaY fatorapK zamaniy~apK TawiylapK
reference (untransliterated): وَ يُمكِنُ أَن تُحصَدَ لثِّمار عَلى مَدى فَترَةِن زَمَنِيَّةِن طَوِيلَةِن
predicted (untransliterated): وَيُمْكِنُ أَنْ تُحْصَدَ الثِّمَار عَلَى مَدَى فَتْرَةٍ زَمَنِيَّةٍ طَوِيلَةٍ
--
reference: wa>Hraza lmarkaza lv~Aliv >alr~iwA}iy~u ljazA}iriy~u >aHmadu TiybAwiy Ean riwAyatihi mawtun nAEim
predicted: wa>aHoraza Alomarokaza Alv~aAlivo >alr~iwaA}iy~u AlojazaA}iriy~u >aHomadu TiybaAwi Eano riwaAyatihi mawotunnaAEimo
reference (untransliterated): وَأحرَزَ لمَركَزَ لثّالِث أَلرِّوائِيُّ لجَزائِرِيُّ أَحمَدُ طِيباوِي عَن رِوايَتِهِ مَوتُن ناعِم
predicted (untransliterated): وَأَحْرَزَ الْمَرْكَزَ الثَّالِثْ أَلرِّوَائِيُّ الْجَزَائِرِيُّ أَحْمَدُ طِيبَاوِ عَنْ رِوَايَتِهِ مَوْتُننَاعِمْ
--
reference: wAxtatama lbarAziyliy~uwna mubArAyAtihimi l<iEdAdiy~apa biAlfawzi EalY SirbyA bihadafin waHiydin saj~alahu lmuhAjimu farydun fiy l$~awTi lv~Aniy mina lmubArApi >al~atiy >uqiymat fiy sAwbAwluw
predicted: waAxotatama AlobaraAziyliy~uwna mubaArayaAtihimi Alo<iEodaAdiy~api biAlofawozi EalaY Sirobiya bihadafK waHiydK saj~alahu AlomuhaAjimu fariydN fiy Al$~awoTi Alv~aAniy mina AlomubaAraApi >al~atiy >uqiymato fiy saAwobaAluw
reference (untransliterated): واختَتَمَ لبَرازِيلِيُّونَ مُباراياتِهِمِ لإِعدادِيَّةَ بِالفَوزِ عَلى صِربيا بِهَدَفِن وَحِيدِن سَجَّلَهُ لمُهاجِمُ فَريدُن فِي لشَّوطِ لثّانِي مِنَ لمُباراةِ أَلَّتِي أُقِيمَت فِي ساوباولُو
predicted (untransliterated): وَاخْتَتَمَ الْبَرَازِيلِيُّونَ مُبَارَيَاتِهِمِ الْإِعْدَادِيَّةِ بِالْفَوْزِ عَلَى صِرْبِيَ بِهَدَفٍ وَحِيدٍ سَجَّلَهُ الْمُهَاجِمُ فَرِيدٌ فِي الشَّوْطِ الثَّانِي مِنَ الْمُبَارَاةِ أَلَّتِي أُقِيمَتْ فِي سَاوْبَالُو
--
reference: wA$tahara lr~AHilu bimaqAlAtihi wakutubihi lr~aSiynapi >al~atiy taDam~anat qirA'Atin mustaqbaliy~apan lil>AfAqi ls~iyAsiy~api wAl<ijtimAEiy~api fiy lEAlami lEarabiy~i l<islAmiy~i
predicted: waA$otahara Alr~aAHilu bimaqaAlaAtihi wakutubihi Alr~aSiynapi >al~atiy taDam~anato qiraA'aAtK musotaqobaliy~apF lilo|faAqi Als~iyaAsiy~api waAlo<ijotimaAEiy~api fiy AloEaAlami AloEarabiy~i Alo<isolaAmiy~i
reference (untransliterated): واشتَهَرَ لرّاحِلُ بِمَقالاتِهِ وَكُتُبِهِ لرَّصِينَةِ أَلَّتِي تَضَمَّنَت قِراءاتِن مُستَقبَلِيَّةَن لِلأافاقِ لسِّياسِيَّةِ والإِجتِماعِيَّةِ فِي لعالَمِ لعَرَبِيِّ لإِسلامِيِّ
predicted (untransliterated): وَاشْتَهَرَ الرَّاحِلُ بِمَقَالَاتِهِ وَكُتُبِهِ الرَّصِينَةِ أَلَّتِي تَضَمَّنَتْ قِرَاءَاتٍ مُسْتَقْبَلِيَّةً لِلْآفَاقِ السِّيَاسِيَّةِ وَالْإِجْتِمَاعِيَّةِ فِي الْعَالَمِ الْعَرَبِيِّ الْإِسْلَامِيِّ
--
reference: wa>aSbaHa ha*A lS~arHu matHafan rasmiy~an
predicted: wa>aSobaHa ha*aA AlS~aroHu matoHafAF rasomiy~AF
reference (untransliterated): وَأَصبَحَ هَذا لصَّرحُ مَتحَفَن رَسمِيَّن
predicted (untransliterated): وَأَصْبَحَ هَذَا الصَّرْحُ مَتْحَفاً رَسْمِيّاً
--
reference: w>aDAfa lbayAnu an~a fariyqaan min l>aTib~A'i wAlmumar~iDAt w<ixtiSASiy~iyna >Axariyna fiy majAli lS~iH~api yaEtanuwna bimAndiyl~A EalY madAri ls~AEapi
predicted: wa>aDaAfa AlobayaAnu >an~a fariyqAF mina Alo>aTib~aA'i waAlomumar~iDaAt waAxotiSaASiy~iyna |xariyna fiy majaAli AlS~iH~api yaEotanuwna bimaAnodil~aA EalaY madaAri Als~aAEapi
reference (untransliterated): وأَضافَ لبَيانُ َنَّ فَرِيقََن مِن لأَطِبّاءِ والمُمَرِّضات وإِختِصاصِيِّينَ أاخَرِينَ فِي مَجالِ لصِّحَّةِ يَعتَنُونَ بِماندِيلّا عَلى مَدارِ لسّاعَةِ
predicted (untransliterated): وَأَضَافَ الْبَيَانُ أَنَّ فَرِيقاً مِنَ الْأَطِبَّاءِ وَالْمُمَرِّضَات وَاخْتِصَاصِيِّينَ آخَرِينَ فِي مَجَالِ الصِّحَّةِ يَعْتَنُونَ بِمَانْدِلَّا عَلَى مَدَارِ السَّاعَةِ
--
reference: wAEtabaruwhA falsafapan ruwHiy~apan mutakAmilapan litaHriyri ljismi wAlfikr
predicted: waAEotabaruwhaA falosafapF ruwHiy~apF mutakaAmilapF litaHoriyri Alojisomi waAlofikor
reference (untransliterated): واعتَبَرُوها فَلسَفَةَن رُوحِيَّةَن مُتَكامِلَةَن لِتَحرِيرِ لجِسمِ والفِكر
predicted (untransliterated): وَاعْتَبَرُوهَا فَلْسَفَةً رُوحِيَّةً مُتَكَامِلَةً لِتَحْرِيرِ الْجِسْمِ وَالْفِكْر
--
reference: >alt~awaH~udu huwa majmuwEapu DTirAbAtin EaSabiy~apin fiy lt~aTaw~ur ta$malu >aErADuhA wujuwda ma$Akila fiy ls~uluwki lAjtimAEiy~i lil$~axSi lmuSAb
predicted: >alt~awaH~udu huwa majomuwEapu AlT~iraAbaAtK EaSabiy~apK fiy Alt~aTaw~uro ta$omalu >aEoraADuhaA bujuwda ma$aAkila fiy Als~uluwki Alo<ijotimaAEiy~i lil$~axoSi AlomuSaAbo
reference (untransliterated): أَلتَّوَحُّدُ هُوَ مَجمُوعَةُ ضطِراباتِن عَصَبِيَّةِن فِي لتَّطَوُّر تَشمَلُ أَعراضُها وُجُودَ مَشاكِلَ فِي لسُّلُوكِ لاجتِماعِيِّ لِلشَّخصِ لمُصاب
predicted (untransliterated): أَلتَّوَحُّدُ هُوَ مَجْمُوعَةُ الطِّرَابَاتٍ عَصَبِيَّةٍ فِي التَّطَوُّرْ تَشْمَلُ أَعْرَاضُهَا بُجُودَ مَشَاكِلَ فِي السُّلُوكِ الْإِجْتِمَاعِيِّ لِلشَّخْصِ الْمُصَابْ
--
reference: wAlEamalu lr~a}iysiy~u lahu huwa riwAyatahu lmalHamiy~apu mA}apu EAmin mina lEuzlapi >al~atiy nAla EanhA jA}izapa nuwbila fiy l>adab EAma >alfin watisEimi}apin wa<ivnAni wavamAnuwn
predicted: waAloEamalu Alr~a}iysiy~u lahu huwa riwaAyatahu AlomaloHamiy~apu ma>apu EaAmK mina AloEuzolapi >al~atiy naAla EanohaA jaA}izapa nuwbila fiy Alo>adabo EaAma >alofK watisoEi ma}apK wa<ivnaAni wavamAnuwna
reference (untransliterated): والعَمَلُ لرَّئِيسِيُّ لَهُ هُوَ رِوايَتَهُ لمَلحَمِيَّةُ مائَةُ عامِن مِنَ لعُزلَةِ أَلَّتِي نالَ عَنها جائِزَةَ نُوبِلَ فِي لأَدَب عامَ أَلفِن وَتِسعِمِئَةِن وَإِثنانِ وَثَمانُون
predicted (untransliterated): وَالْعَمَلُ الرَّئِيسِيُّ لَهُ هُوَ رِوَايَتَهُ الْمَلْحَمِيَّةُ مَأَةُ عَامٍ مِنَ الْعُزْلَةِ أَلَّتِي نَالَ عَنْهَا جَائِزَةَ نُوبِلَ فِي الْأَدَبْ عَامَ أَلْفٍ وَتِسْعِ مَئَةٍ وَإِثنَانِ وَثَمانُونَ
--
reference: wAlmiykuwng was>aluwyn fiy januwbi $arqi >AsyA
predicted: waAlomiykuwnogo wasaAluwiyno fiy januwbi $aroqi |soyaA
reference (untransliterated): والمِيكُونغ وَسأَلُوين فِي جَنُوبِ شَرقِ أاسيا
predicted (untransliterated): وَالْمِيكُونْغْ وَسَالُوِينْ فِي جَنُوبِ شَرْقِ آسْيَا
--
reference: wa>n~a >aham~a muEaw~iqAti najAHihA takmunu fiy Eadami tafar~ugi >aSHAbihA li<idAratihA
predicted: wa>an~a >aham~a muEaw~iqaAti najaAHihaA takomunu fiy Eadami tafar~ugi >aSoHaAbihaA li<idaAratihaA
reference (untransliterated): وَأنَّ أَهَمَّ مُعَوِّقاتِ نَجاحِها تَكمُنُ فِي عَدَمِ تَفَرُّغِ أَصحابِها لِإِدارَتِها
predicted (untransliterated): وَأَنَّ أَهَمَّ مُعَوِّقَاتِ نَجَاحِهَا تَكْمُنُ فِي عَدَمِ تَفَرُّغِ أَصْحَابِهَا لِإِدَارَتِهَا
--
reference: wa>awDaHa lbAHivuwna >an~a suw'a lt~ag*iyapi huwa ls~ababu lr~a}iysiy~u litawaq~ufi ln~umuw Einda l>aTfAl
predicted: wa>awoDaHa AlobaAHivuwna >an~a suw'a Alt~ago*iyapi huwa Als~ababu Alr~a}iysiy~u litawaq~ufi Aln~umuw Einoda Alo>aTofaAlo
reference (untransliterated): وَأَوضَحَ لباحِثُونَ أَنَّ سُوءَ لتَّغذِيَةِ هُوَ لسَّبَبُ لرَّئِيسِيُّ لِتَوَقُّفِ لنُّمُو عِندَ لأَطفال
predicted (untransliterated): وَأَوْضَحَ الْبَاحِثُونَ أَنَّ سُوءَ التَّغْذِيَةِ هُوَ السَّبَبُ الرَّئِيسِيُّ لِتَوَقُّفِ النُّمُو عِنْدَ الْأَطْفَالْ
--
reference: wa>awDaHati lmajal~apu >an~a ls~ababa fiy *alika yarjiEu <ilY taDay~uqi l$~uEabi lhawA}iy~api wata$an~ujihA bifiEli lhawA'i lbArid
predicted: wa>awoDaHati Alomajal~apu >an~a Als~ababa fiy *alika yarojiEu <ilaY taDay~uqi Al$~uEabi AlohawaA}iy~api wata$an~ujihaA bifiEoli AlohawaA'i AlobaArid
reference (untransliterated): وَأَوضَحَتِ لمَجَلَّةُ أَنَّ لسَّبَبَ فِي ذَلِكَ يَرجِعُ إِلى تَضَيُّقِ لشُّعَبِ لهَوائِيَّةِ وَتَشَنُّجِها بِفِعلِ لهَواءِ لبارِد
predicted (untransliterated): وَأَوْضَحَتِ الْمَجَلَّةُ أَنَّ السَّبَبَ فِي ذَلِكَ يَرْجِعُ إِلَى تَضَيُّقِ الشُّعَبِ الْهَوَائِيَّةِ وَتَشَنُّجِهَا بِفِعْلِ الْهَوَاءِ الْبَارِد
--
reference: wabAta >atlitiykuw madriyd fiy SadArapi lt~artiybi lEAm~i bi>arbaEi niqAT
predicted: wabaAta >atolitiykuw madoriydo fiy SadaArapi Alt~arotiybi AloEaAm~i bi>arobaEi niqaAT
reference (untransliterated): وَباتَ أَتلِتِيكُو مَدرِيد فِي صَدارَةِ لتَّرتِيبِ لعامِّ بِأَربَعِ نِقاط
predicted (untransliterated): وَبَاتَ أَتْلِتِيكُو مَدْرِيدْ فِي صَدَارَةِ التَّرْتِيبِ الْعَامِّ بِأَرْبَعِ نِقَاط
--
reference: wabiAlt~Aliy tusAEidu EalY lwiqAyapi mina l<imsAk
predicted: wabiAt~aAliy tusaAEidu EalaY AlowiyqaAyapi mina Alo<imosaAko
reference (untransliterated): وَبِالتّالِي تُساعِدُ عَلى لوِقايَةِ مِنَ لإِمساك
predicted (untransliterated): وَبِاتَّالِي تُسَاعِدُ عَلَى الْوِيقَايَةِ مِنَ الْإِمْسَاكْ
--
reference: wa*alika biziyArapi jumhuwrin xAS~in jid~an sanawiy~an
predicted: wa*alika biziyaArapi jumohuwrK xaAS~K jid~AF sanawiy~AF
reference (untransliterated): وَذَلِكَ بِزِيارَةِ جُمهُورِن خاصِّن جِدَّن سَنَوِيَّن
predicted (untransliterated): وَذَلِكَ بِزِيَارَةِ جُمْهُورٍ خَاصٍّ جِدّاً سَنَوِيّاً
--
reference: wabisababi $ukuwkin bi>an~a lT~A}irapa kAnat tuqil~u idwArd snuwdun >al~a*iy tat~ahimuhu wA$inTun biAlt~ajas~us
predicted: wabisababi $ukuwkK bi>an~a AlT~aA}irapa kaAna Alt~uqil~u <idowaAbo snuwduno >al~a*iy tat~ahimuhu wa $inoTun biAlt~ajas~us
reference (untransliterated): وَبِسَبَبِ شُكُوكِن بِأَنَّ لطّائِرَةَ كانَت تُقِلُّ ِدوارد سنُودُن أَلَّذِي تَتَّهِمُهُ واشِنطُن بِالتَّجَسُّس
predicted (untransliterated): وَبِسَبَبِ شُكُوكٍ بِأَنَّ الطَّائِرَةَ كَانَ التُّقِلُّ إِدْوَابْ سنُودُنْ أَلَّذِي تَتَّهِمُهُ وَ شِنْطُن بِالتَّجَسُّس
--
reference: wabaEavuwA risAlapan <ilY lra~}iysi tataDama~nu maTAliba liEawdatihim
predicted: wabaEavuwA risaAlapF <ilaY Alr~a}iysi tataDam~anu maTaAliba liEawodatihimo
reference (untransliterated): وَبَعَثُوا رِسالَةَن إِلى لرَّئِيسِ تَتَضَمَّنُ مَطالِبَ لِعَودَتِهِم
predicted (untransliterated): وَبَعَثُوا رِسَالَةً إِلَى الرَّئِيسِ تَتَضَمَّنُ مَطَالِبَ لِعَوْدَتِهِمْ
--
reference: wabaEda $uhuwrin mina lHayrapi wAlqalaq taEara~fa kuwmAr EalY markazi Eabdi llhi bni zaydi lva~qAfiy~i lilta~Eriyfi biAl<islAm
predicted: wabaEoda $uhuwrK mina AloHayorapi waAloqalaqo taEar~afa kuwmaAra EalaY marokazi Eabodi All~aAhi bonizayodi Alv~aqaAfiy~i lilt~aEoriyfi biAlo<isolaAmo
reference (untransliterated): وَبَعدَ شُهُورِن مِنَ لحَيرَةِ والقَلَق تَعَرَّفَ كُومار عَلى مَركَزِ عَبدِ للهِ بنِ زَيدِ لثَّقافِيِّ لِلتَّعرِيفِ بِالإِسلام
predicted (untransliterated): وَبَعْدَ شُهُورٍ مِنَ الْحَيْرَةِ وَالْقَلَقْ تَعَرَّفَ كُومَارَ عَلَى مَرْكَزِ عَبْدِ اللَّاهِ بْنِزَيْدِ الثَّقَافِيِّ لِلتَّعْرِيفِ بِالْإِسْلَامْ
--
reference: wabiha*A yabqY mi}apun wasit~apun wav~l>avuwna muHtajazan fiy lmuEtaqali lmuviyri liljadal
predicted: wabiha*A yaboqaY mi}apN wasit~apN wavalaAvuwna muHotajazAF fiy AlomuEotaqali Alomuviyri lilojadaYlo
reference (untransliterated): وَبِهَذا يَبقى مِئَةُن وَسِتَّةُن وَثّلأَثُونَ مُحتَجَزَن فِي لمُعتَقَلِ لمُثِيرِ لِلجَدَل
predicted (untransliterated): وَبِهَذا يَبْقَى مِئَةٌ وَسِتَّةٌ وَثَلَاثُونَ مُحْتَجَزاً فِي الْمُعْتَقَلِ الْمُثِيرِ لِلْجَدَىلْ
--
reference: watustaxdamu fiy baEDi ld~uwal wasA}ilu EilAjin muxtalifapun
predicted: watusotaxodamu fiy baEoDi Ald~uwalo wasaA}ilu EilaAjK muxotalifapN
reference (untransliterated): وَتُستَخدَمُ فِي بَعضِ لدُّوَل وَسائِلُ عِلاجِن مُختَلِفَةُن
predicted (untransliterated): وَتُسْتَخْدَمُ فِي بَعْضِ الدُّوَلْ وَسَائِلُ عِلَاجٍ مُخْتَلِفَةٌ
--
reference: wataTaw~ara stixdAmu lT~A}irAti lEAmilapi biduwni Tay~Ar wabada>ati ls~AEAtu l*~akiy~apu al<inti$Ara waka*alika lT~ibAEapu lv~ulAviy~apu l>abEAd
predicted: wataTaw~ara AsotixodaAmu AlT~aA}iraAti AloEaAmilapi biduwni Tay~aAr wabada>ati Als~aAEaAtu Al*~akiy~apu Alo<inoti$aAra waka*alika AlT~ibaAEapu Alv~ulAviy~apu Al>aboEAd
reference (untransliterated): وَتَطَوَّرَ ستِخدامُ لطّائِراتِ لعامِلَةِ بِدُونِ طَيّار وَبَدَأَتِ لسّاعاتُ لذَّكِيَّةُ َلإِنتِشارَ وَكَذَلِكَ لطِّباعَةُ لثُّلاثِيَّةُ لأَبعاد
predicted (untransliterated): وَتَطَوَّرَ اسْتِخْدَامُ الطَّائِرَاتِ الْعَامِلَةِ بِدُونِ طَيَّار وَبَدَأَتِ السَّاعَاتُ الذَّكِيَّةُ الْإِنْتِشَارَ وَكَذَلِكَ الطِّبَاعَةُ الثُّلاثِيَّةُ الأَبْعاد
--
reference: wajA'a ha*A lqarAr baEda <iElAni lsa~Euwdiya~pi taxfiyDa >aEdAdi lHuja~Aji ha*A lEAm
predicted: wajaA'a ha*aA AloqaraAro baEoda <iEolaAni Als~uEuwdiy~api taxofiyDa >aEodaAdi AloHuj~aAji ha*aA AloEaAmo
reference (untransliterated): وَجاءَ هَذا لقَرار بَعدَ إِعلانِ لسَّعُودِيَّةِ تَخفِيضَ أَعدادِ لحُجَّاجِ هَذا لعام
predicted (untransliterated): وَجَاءَ هَذَا الْقَرَارْ بَعْدَ إِعْلَانِ السُّعُودِيَّةِ تَخْفِيضَ أَعْدَادِ الْحُجَّاجِ هَذَا الْعَامْ
--
reference: wajA'ati l>arqAmu SAdimapan fiy mA yaxuS~u l$~arqa l>awsaT
predicted: wajaA'api Alo>aroqaAmu SaAdimapF fiymaA yaxuS~u Al$~aroqa Alo>awoSaTo
reference (untransliterated): وَجاءَتِ لأَرقامُ صادِمَةَن فِي ما يَخُصُّ لشَّرقَ لأَوسَط
predicted (untransliterated): وَجَاءَةِ الْأَرْقَامُ صَادِمَةً فِيمَا يَخُصُّ الشَّرْقَ الْأَوْصَطْ
--
reference: waSadarati lr~asA}il bi<ismi mubdiEiy wafan~Aniy miSra
predicted: wasaDarati Alr~asaA'ilo bi<isomi mubodiEi wafan~aAniy miSora
reference (untransliterated): وَصَدَرَتِ لرَّسائِل بِإِسمِ مُبدِعِي وَفَنّانِي مِصرَ
predicted (untransliterated): وَسَضَرَتِ الرَّسَاءِلْ بِإِسْمِ مُبْدِعِ وَفَنَّانِي مِصْرَ
--
reference: wafiy ftitAHi lmu&tamari qAlati l$~AEirapu $ariyfapa ls~ay~id <in~a lEaq~Ada it~axa*a mina lqirA'api wAl<iT~ilAEi EalY kul~i lEuluwm wamuxtalafi lHaDArAt silAHan yuHaT~imu bihi lS~anamiy~apa wayaksiru lmuHar~amAt
predicted: wafiy AfotitaAHi Alomu&otamari qaAlati Al$~aAEirapu $ariyfapa Als~ay~ido <in~a AloEaq~aAda Alt~axa*a mina AloqiraA'api waliADoTilaAEi EalaY kul~i AloEuluwmo wamuxotalifi AloHaDaAraAt silaAHAF yuHaT~i mgubihi AlS~anamiy~apa wayakosiru AlomuHar~amaAt
reference (untransliterated): وَفِي فتِتاحِ لمُؤتَمَرِ قالَتِ لشّاعِرَةُ شَرِيفَةَ لسَّيِّد إِنَّ لعَقّادَ ِتَّخَذَ مِنَ لقِراءَةِ والإِطِّلاعِ عَلى كُلِّ لعُلُوم وَمُختَلَفِ لحَضارات سِلاحَن يُحَطِّمُ بِهِ لصَّنَمِيَّةَ وَيَكسِرُ لمُحَرَّمات
predicted (untransliterated): وَفِي افْتِتَاحِ الْمُؤْتَمَرِ قَالَتِ الشَّاعِرَةُ شَرِيفَةَ السَّيِّدْ إِنَّ الْعَقَّادَ التَّخَذَ مِنَ الْقِرَاءَةِ وَلِاضْطِلَاعِ عَلَى كُلِّ الْعُلُومْ وَمُخْتَلِفِ الْحَضَارَات سِلَاحاً يُحَطِّ مغُبِهِ الصَّنَمِيَّةَ وَيَكْسِرُ الْمُحَرَّمَات
--
reference: wafiy kuwryA ljanuwbiy~api taquwmu lHukuwmapu bitamwiyli musta$fayAtin liEilAji ha*A l<idmAni l~a*iy yuEtabaru mu$kilapan qawmiy~apan
predicted: wafiy kuwriyaA Alojanuwbiy~api taquwmu AloHukuwmapu bitamowiyli musota$ofayaAtK liEilaAji ha*aA Alo<idomaAni Al~a*iy yuEotabaru mu$okilapF qawomiy~apF
reference (untransliterated): وَفِي كُوريا لجَنُوبِيَّةِ تَقُومُ لحُكُومَةُ بِتَموِيلِ مُستَشفَياتِن لِعِلاجِ هَذا لإِدمانِ لَّذِي يُعتَبَرُ مُشكِلَةَن قَومِيَّةَن
predicted (untransliterated): وَفِي كُورِيَا الْجَنُوبِيَّةِ تَقُومُ الْحُكُومَةُ بِتَمْوِيلِ مُسْتَشْفَيَاتٍ لِعِلَاجِ هَذَا الْإِدْمَانِ الَّذِي يُعْتَبَرُ مُشْكِلَةً قَوْمِيَّةً
--
reference: wakAna l>amalu >an takuwna ha*ihi ld~iymuqrATiy~Atu maSHuwbapan bi>adA'in tanmawiy~in muxtalif
predicted: wakAna Alo>amalu >ano takuwna ha*ihi Ald~iymuwqoraATiy~aAtu maSoHuwbapF bi>adaA'K tF mawiy~K muxotalifo
reference (untransliterated): وَكانَ لأَمَلُ أَن تَكُونَ هَذِهِ لدِّيمُقراطِيّاتُ مَصحُوبَةَن بِأَداءِن تَنمَوِيِّن مُختَلِف
predicted (untransliterated): وَكانَ الْأَمَلُ أَنْ تَكُونَ هَذِهِ الدِّيمُوقْرَاطِيَّاتُ مَصْحُوبَةً بِأَدَاءٍ تً مَوِيٍّ مُخْتَلِفْ
--
reference: wakatabuwA fiy dawriy~api lkul~iy~api l>amiyrikiy~api li>amrADi lqalb >an~a ls~umnapa tartabiTu biHuduwvi tagayiyrAt fiy lqalbi ladY lbAligiyn
predicted: wakatabuwA fiy daworiy~api Alokul~iy~api Alo>amiyriykiy~api li>amoraADi Aloqalo >an~a Als~umonapa tarotabiTu biHuduwvi tagoyiyraAt fiy Aloqalobi ladaY AlobaAligiyno
reference (untransliterated): وَكَتَبُوا فِي دَورِيَّةِ لكُلِّيَّةِ لأَمِيرِكِيَّةِ لِأَمراضِ لقَلب أَنَّ لسُّمنَةَ تَرتَبِطُ بِحُدُوثِ تَغَيِيرات فِي لقَلبِ لَدى لبالِغِين
predicted (untransliterated): وَكَتَبُوا فِي دَوْرِيَّةِ الْكُلِّيَّةِ الْأَمِيرِيكِيَّةِ لِأَمْرَاضِ الْقَلْ أَنَّ السُّمْنَةَ تَرْتَبِطُ بِحُدُوثِ تَغْيِيرَات فِي الْقَلْبِ لَدَى الْبَالِغِينْ
--
reference: wakul~u *alika bimuHtawYan munxafiDin lilgAyapi mina ls~uErAti lHarAriy~api
predicted: wakul~u *alika bimuHotawAF munoxafiDK lilogaAyapi mina Als~uEoraAti AloHaraAriy~api
reference (untransliterated): وَكُلُّ ذَلِكَ بِمُحتَوىَن مُنخَفِضِن لِلغايَةِ مِنَ لسُّعراتِ لحَرارِيَّةِ
predicted (untransliterated): وَكُلُّ ذَلِكَ بِمُحْتَواً مُنْخَفِضٍ لِلْغَايَةِ مِنَ السُّعْرَاتِ الْحَرَارِيَّةِ
--
reference: wakul~amA zAdat kamiy~apu ls~uk~ari lmutanAwalapi maEa lt~amri taqil~u fA}idatuhu lgi*A}iy~apu
predicted: wakul~amaA zaAdato kam~ay~apu Als~uk~ari AlomutanaAwalapi maEa Alotamori taqil~u faA}idatuhu Alogi*aA}iy~apu
reference (untransliterated): وَكُلَّما زادَت كَمِيَّةُ لسُّكَّرِ لمُتَناوَلَةِ مَعَ لتَّمرِ تَقِلُّ فائِدَتُهُ لغِذائِيَّةُ
predicted (untransliterated): وَكُلَّمَا زَادَتْ كَمَّيَّةُ السُّكَّرِ الْمُتَنَاوَلَةِ مَعَ الْتَمْرِ تَقِلُّ فَائِدَتُهُ الْغِذَائِيَّةُ
--
reference: walA yazAlu ha*A lbaladu mutamas~ikan bitaqwiymi lkaniysapi lqibTiy~api >almaEruwfi maHal~iy~an biAlt~aqwiymi l<ivyuwbiy~i
predicted: walaA yazaAlu ha*aA Alobaladu mutamas~ikAF bitaqowiymi Alokaniysapi AloqiboTiy~api >alomaEoruwfi maHal~iy~AF biAlt~aqowiymi Alo<ivoyuwbiy~i
reference (untransliterated): وَلا يَزالُ هَذا لبَلَدُ مُتَمَسِّكَن بِتَقوِيمِ لكَنِيسَةِ لقِبطِيَّةِ أَلمَعرُوفِ مَحَلِّيَّن بِالتَّقوِيمِ لإِثيُوبِيِّ
predicted (untransliterated): وَلَا يَزَالُ هَذَا الْبَلَدُ مُتَمَسِّكاً بِتَقْوِيمِ الْكَنِيسَةِ الْقِبْطِيَّةِ أَلْمَعْرُوفِ مَحَلِّيّاً بِالتَّقْوِيمِ الْإِثْيُوبِيِّ
--
reference: walaEibati lxibrapu dawrahA fiy tatwiyji EA$uwra lxAmisi EAlamiy~an
predicted: walaEibapi Aloxiborapu daworahaA fiy tatowiyji EaA$uwra AloxaAmisi EaAlamiy~AF
reference (untransliterated): وَلَعِبَتِ لخِبرَةُ دَورَها فِي تَتوِيجِ عاشُورَ لخامِسِ عالَمِيَّن
predicted (untransliterated): وَلَعِبَةِ الْخِبْرَةُ دَوْرَهَا فِي تَتْوِيجِ عَاشُورَ الْخَامِسِ عَالَمِيّاً
--
reference: tatawAlY lEamalyAtu ls~ir~iyapa biAlHuduwv
predicted: tatawaAlaY AloEamaliy~aAtu Als~ir~iy~apu biAloHuduwv
reference (untransliterated): تَتَوالى لعَمَلياتُ لسِّرِّيَةَ بِالحُدُوث
predicted (untransliterated): تَتَوَالَى الْعَمَلِيَّاتُ السِّرِّيَّةُ بِالْحُدُوث
--
reference: wamin tilka ls~ilaE >al$~Ayu lS~iyniy~u wAlwaraqu wAlbAruwdu wAlbuwSilapu
predicted: wamino tiloka Als~ilaE >al$~aAyu AlS~iyniy~u waAlowaraqu waAlobaAruwdu waAlobuwSilapu
reference (untransliterated): وَمِن تِلكَ لسِّلَع أَلشّايُ لصِّينِيُّ والوَرَقُ والبارُودُ والبُوصِلَةُ
predicted (untransliterated): وَمِنْ تِلْكَ السِّلَع أَلشَّايُ الصِّينِيُّ وَالْوَرَقُ وَالْبَارُودُ وَالْبُوصِلَةُ
--
reference: wamanaHa >AbA}uhumu lqudrapa EalY lt~aHak~umi fiy kayfiy~api stixdAmi ha*ihi lxidmapi
predicted: wamanaHa |baA&uhumu Aloqudorapa EalaY Alt~aHak~umi fiy kayofiy~api AsotixodaAmi ha*ihi Aloxidomapi
reference (untransliterated): وَمَنَحَ أابائُهُمُ لقُدرَةَ عَلى لتَّحَكُّمِ فِي كَيفِيَّةِ ستِخدامِ هَذِهِ لخِدمَةِ
predicted (untransliterated): وَمَنَحَ آبَاؤُهُمُ الْقُدْرَةَ عَلَى التَّحَكُّمِ فِي كَيْفِيَّةِ اسْتِخْدَامِ هَذِهِ الْخِدْمَةِ
--
reference: waya>mulu lbAHivuwna taTwiyra Hubuwbin >aw nusxapin mina ld~awA' qAbilapan lilHaqni xilAla xamsi sanawAt
predicted: waya>omulu AlobaAHivuwna taTowiyra HuwuwbK >awo nusoxapK mina Ald~awaA qaAbilapF liloHaqoni xilaAla xamosi sanawaAt
reference (untransliterated): وَيَأمُلُ لباحِثُونَ تَطوِيرَ حُبُوبِن أَو نُسخَةِن مِنَ لدَّواء قابِلَةَن لِلحَقنِ خِلالَ خَمسِ سَنَوات
predicted (untransliterated): وَيَأْمُلُ الْبَاحِثُونَ تَطْوِيرَ حُوُوبٍ أَوْ نُسْخَةٍ مِنَ الدَّوَا قَابِلَةً لِلْحَقْنِ خِلَالَ خَمْسِ سَنَوَات
--
reference: wayastaxdimu lbarnAmaju niZAman saHAbiy~an lil*~akA'i lS~unEiy~i yasmaHu lahu bitaHliyli l<iymA'Ati wAlt~aEAbiyr
predicted: wayasotaxodimu AlobaronaAmaju niZaAmAF saHaAbiy~AF lil*~akaA'i AlS~unoEiy~i yasomaHu lahu bitaHoliyli Alo<iymaA'aAti waAlt~aEaAbiyro
reference (untransliterated): وَيَستَخدِمُ لبَرنامَجُ نِظامَن سَحابِيَّن لِلذَّكاءِ لصُّنعِيِّ يَسمَحُ لَهُ بِتَحلِيلِ لإِيماءاتِ والتَّعابِير
predicted (untransliterated): وَيَسْتَخْدِمُ الْبَرْنَامَجُ نِظَاماً سَحَابِيّاً لِلذَّكَاءِ الصُّنْعِيِّ يَسْمَحُ لَهُ بِتَحْلِيلِ الْإِيمَاءَاتِ وَالتَّعَابِيرْ
--
reference: wayuEtabaru mihrajAnu qarTAja ls~iynamA}iy~u min >aEraqi mihrajAnAti >afriyqyA
predicted: wayuEotabaru mihorajaAnu qaroTaAja Als~iynamaA}iy~u mino >aEoraqi mihorajaAnaAti >afriyqoyaA
reference (untransliterated): وَيُعتَبَرُ مِهرَجانُ قَرطاجَ لسِّينَمائِيُّ مِن أَعرَقِ مِهرَجاناتِ أَفرِيقيا
predicted (untransliterated): وَيُعْتَبَرُ مِهْرَجَانُ قَرْطَاجَ السِّينَمَائِيُّ مِنْ أَعْرَقِ مِهْرَجَانَاتِ أَفرِيقْيَا
--
reference: wayaquwlu lEulamA'u <in~ahu min gayri lmuraj~aHi >an tuTaw~ira lbaktiyryA lmuEdiyapu muqAwamapan Did~a lEilAji ljadiyd >al~a*iy >aSbaHa mutAHan biAlfiEl fiy $akli marhamin lil>amrADi ljildiy~api
predicted: wayaquwlu AloEulamaA'u <in~ahu mino gayori Alomuraj~aHi >ano tuTaw~ira AlobakotiyroyaA AlomuEodiyapu muqaAwamapF Did~a AloEilaAji lojadiyd >al~a*iy >aSobaHa mutaAHAF biAlofiEol fiy $akoli marohamK lilo>amoraADi Alojiylodiy~api
reference (untransliterated): وَيَقُولُ لعُلَماءُ إِنَّهُ مِن غَيرِ لمُرَجَّحِ أَن تُطَوِّرَ لبَكتِيريا لمُعدِيَةُ مُقاوَمَةَن ضِدَّ لعِلاجِ لجَدِيد أَلَّذِي أَصبَحَ مُتاحَن بِالفِعل فِي شَكلِ مَرهَمِن لِلأَمراضِ لجِلدِيَّةِ
predicted (untransliterated): وَيَقُولُ الْعُلَمَاءُ إِنَّهُ مِنْ غَيْرِ الْمُرَجَّحِ أَنْ تُطَوِّرَ الْبَكْتِيرْيَا الْمُعْدِيَةُ مُقَاوَمَةً ضِدَّ الْعِلَاجِ لْجَدِيد أَلَّذِي أَصْبَحَ مُتَاحاً بِالْفِعْل فِي شَكْلِ مَرْهَمٍ لِلْأَمْرَاضِ الْجِيلْدِيَّةِ
--
reference: wayumkinuka lHuSuwlu EalY taTbiyqAtin lilt~adriybAti l>asAsiy~api maj~Anan
predicted: wayumokinuka AloHuSuwlu EalaY taTobiyqaAtK liltadoriybaAti Alo>asaAsiy~api maj~aAnAF
reference (untransliterated): وَيُمكِنُكَ لحُصُولُ عَلى تَطبِيقاتِن لِلتَّدرِيباتِ لأَساسِيَّةِ مَجّانَن
predicted (untransliterated): وَيُمْكِنُكَ الْحُصُولُ عَلَى تَطْبِيقَاتٍ لِلتَدْرِيبَاتِ الْأَسَاسِيَّةِ مَجَّاناً
--
```

## Fine-Tuning Script

You can find the script used to produce this model
[here](https://github.com/elgeish/transformers/blob/cfc0bd01f2ac2ea3a5acc578ef2e204bf4304de7/examples/research_projects/wav2vec2/finetune_base_arabic_speech_corpus.sh).
