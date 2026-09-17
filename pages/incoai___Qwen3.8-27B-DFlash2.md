category:: LLM
website:: [HuggingFace](https://huggingface.co/incoai/Qwen3.8-27B-DFlash2) [魔塔社区](https://www.modelscope.cn/models/incoai/Qwen3.8-27B-DFlash2-GGUF)

- # 使用
	- [[llama.cpp]]
		- ```shell
		  MODEL="/data/models/Qwen3.8-27B-GGUF/Qwen3.8-27B-UD-Q4_K_M.gguf"
		  DRAFT="/data/models/Qwen3.8-27B-DFlash2-GGUF/Qwen3.8-27B-DFlash2-Q4_K_M.gguf"
		  
		  HIP_VISIBLE_DEVICES=0 \
		  ./build/bin/llama-server \
		    -m "$MODEL" \
		    -md "$DRAFT" \
		    --device ROCm0 \
		    --spec-draft-device ROCm0 \
		    -ngl all \
		    --spec-draft-ngl all \
		    --spec-type draft-dflash \
		    --spec-draft-n-max 7 \
		    --spec-draft-p-min 0 \
		    --flash-attn on \
		    --jinja \
		    -c 32768 \
		    -np 1 \
		    -b 2048 \
		    -ub 512 \
		    --host 0.0.0.0 \
		    --port 8080 \
		    --alias qwen3.8
		  
		  ```