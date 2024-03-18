# Deep Learning based Quark-Gluon Classification


## Dataset structure

The dataset consists of several parquet files that contain 4 columns - 3 feature columns and 1 Label column

The schema of the dataset is:

```
<pyarrow._parquet.ParquetSchema object at 0x7fb95f035b00>
required group field_id=-1 schema {
  optional group field_id=-1 X_jets (List) {
    repeated group field_id=-1 list {
      optional group field_id=-1 item (List) {
        repeated group field_id=-1 list {
          optional group field_id=-1 item (List) {
            repeated group field_id=-1 list {
              optional double field_id=-1 item;
            }
          }
        }
      }
    }
  }
  optional double field_id=-1 pt;
  optional double field_id=-1 m0;
  optional double field_id=-1 y;
}
```

The column `X_jets` contains nested array which can be rearranged to `125x125` matrices in 3-channel images for 2 classes of particles, quarks and gluons, impinging on a calorimeter.



## Comparing Model performance

As can be seen from the table below, the ResNet model achieves a higher accuracy compared to the VGG model. 
Additionally, ResNet has a smaller architecture, making it faster in terms of computation when compared to VGG.

| Model        | Test Accuracy |
|-----------------------------|------------|
| Resnet    | 72.41666666%     |
| VGG (12 Layer)   | 72.21%    |
