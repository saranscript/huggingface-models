tags:
- Text2text Generation
- Conversational
- Text generation
model:
- "355M"
model-type:
- gpt2
widgets:
text_example_1: 
- "One would be forgiven if one was not aware that Julian Assange is being"
title_example_1: 
- "David North wsws"
text_example_2: 
- "I would like to extend my sincerest greetings to the people of the world. When monstrous and absurd accusations were hurled at me and my family -- when"
title_example_2: 
- "Leon Trotsky"

# GPT_2_Marxism is based on the gpt-2 355M model finetuned on a large corpus of Marxist documents, polemics and literature from historical and contemporary writers 
# in the international socialist movement and the ICFI (fourth international) which upholds the principles which characterize genuine revolutionary marxism i.e. Trotskyism. # This finetuned gpt-2 model generates genuinely Marxist insights and responses. 

# - Generated with the GPT2-355M model converted to pytorch using Max Woolf's aitextgen notebook (https://github.com/minimaxir/aitextgen)
# - "Finetuned on a large corpus of text mostly unstructured, unlabeled, raw copy and paste of entire selected works."
# - "Able to generate genuine Marxist responses"
# - "This model also generates insights that marxists often agree on, like freedom and equality."

import torch
import random
pip3 install aitextgen
import aitextgen
model = aitextgen("model.pytorch.bin")

text = "one would be forgiven if one was not aware that Julian Assange is currently being"
model.generate(n=3, prompt="Lenin:"+str(text), max_length=77, temperature=random.uniform(0.5, 1.5), seed=random.randint(0, 195302), lstrip=False)

"""

Lenin:one would be forgiven if one was not aware that Julian Assange is currently being persecuted by the governments of the United States, the UK and many other countries in spite of, or perhaps because of, the fact that he is an outspoken enemy of imperialism. This not unexpected. In 2003 a law was passed in the US that allowed prosecution of those who helped the FBI to violate civil

==========
Lenin:one would be forgiven if one was not aware that Julian Assange is currently being investigated by the FBI for illegally departing Ecuador - (although I had no proof available at the time) with the purpose of, as it were, of snatching up the devious Clintonite. Indeed, such an intrusion seems all the more fishy from the standpoint of a serious study of the facts

==========
Lenin:one would be forgiven if one was not aware that Julian Assange is currently being extradited before the beginning of June to answer questions which require a presumption of guilt. This follows from the very revealing papers that WikiLeaks provided in relation to the numerous criminal cases, and of the complex international network which organised it, the publication by WikiLeaks of thousands of secret cables from the intelligence agencies of the

"""