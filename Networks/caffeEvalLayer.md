```
layer {
  name: "detection_eval"
  type: "DetectionEvaluate"
  bottom: "detection_out"
  bottom: "label"
  top: "detection_eval"
  include {
    phase: TEST
  }
  detection_evaluate_param {
    num_classes: 5
    background_label_id: 0
    overlap_threshold: 0.5
    evaluate_difficult_gt: false
    name_size_file: "/home/wei/data/car1920*1200/vis/test_name_size.txt"
  }
}
```

