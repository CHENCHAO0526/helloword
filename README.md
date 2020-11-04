# 测试LaneRPN结果:
python tools/test.py ${CONFIG_FILE} &{CHECKPOINT_FILE} --out ***.pkl   得到输出的pkl文件  
eg: python tools/test.py lane_config/remove_y_w10_rpn_lane_weight_angle_5_97_90.py work_dirs/remove_y_w10_rpn_lane_9790/latest.pth --out tmp/remove_y.pkl  
# 测试LaneRPN的recall：  
python tools/eval_metric.py ${CONFIG_FILE} ${PKL_FILE} --eval recall  

# 可视化所有的验证集图片：  
python tools/visualize_result.py ${CONFIG_FILE} ${PKL_FILE}  --out_dir ./tmp/*** --proposal_nums 50  
eg：python tools/visualize_result.py lane_config/remove_y_w10_rpn_lane_weight_angle_5_97_90.py tmp/remove_y.pkl  --out_dir ./tmp/visualize_remove_y_1104 --proposal_nums 100  

# 可视化recall低的图片：  
python tools/low_recall_eval_metric.py ${CONFIG_FILE} ${PKL_FILE} --eval recall --out_dir ./tmp/***  
eg：python tools/low_recall_eval_metric.py lane_config/remove_y_w10_rpn_lane_weight_angle_5_97_90.py tmp/remove_y.pkl --eval recall --out_dir  ./tmp/remove_y_low_recall_1104/

# 训练Lane MaskRCNN : 
python tools/train.py lane_config/lane_mask_rcnn.py
