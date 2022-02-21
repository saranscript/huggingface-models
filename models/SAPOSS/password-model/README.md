# Password-Model

The Password Model is intended to be used with [Credential Digger](https://github.com/SAP/credential-digger) in order to automatically filter false positive password discoveries.

## Model description

[CodeBERT-base-mlm](https://huggingface.co/microsoft/codebert-base-mlm) fine-tuned on a dataset for leak detection.

The aim of this model is to classify whether a code snippet contains a password (i.e., there is a leak) or not. 

## How to use

The model is directly integrated into Credential Digger and can be used to filter the false positive discoveries of a scan.

Please refer to Credential Digger for its usage within the [Python library](https://github.com/SAP/credential-digger#python-library-usage),
the [CLI](https://github.com/SAP/credential-digger/wiki/CLI:--Command-Line-Interface),
or the UI.
