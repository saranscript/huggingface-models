Naming pattern:

1. `GPL/${dataset}-msmarco-distilbert-gpl`: Model with training order of (1) MarginMSE on MSMARCO -> (2) GPL on ${dataset};
2. `GPL/${dataset}-tsdae-msmarco-distilbert-gpl`: Model with training order of (1) TSDAE on ${dataset} -> (2) MarginMSE on MSMARCO -> (3) GPL on ${dataset};
3. `GPL/msmarco-distilbert-margin-mse`: Model trained on MSMARCO with MarginMSE;
4. `GPL/${dataset}-tsdae-msmarco-distilbert-margin-mse`: Model with training order of (1) TSDAE on ${dataset} -> (2) MarginMSE on MSMARCO;

Actually, models in 1. and 2. are built on top of 3. and 4., respectively.


