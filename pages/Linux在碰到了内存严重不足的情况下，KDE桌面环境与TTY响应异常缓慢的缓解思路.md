category:: Notes

- ## 思路一 增大zram配置
	- > 开启或增大 zram（压缩内存交换），比磁盘 swap 卡顿少得多
	- 详见 [[使用zram-generator优雅配置swap]]
- ## 思路二 启用[[systemd-oomd]]主动杀死大内存低优先级的应用
	- > 基于 PSI（压力指标）提前杀进程，比传统 OOM 更“早”。