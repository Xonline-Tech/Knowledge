category:: Notes

- 在使用 [[NPM]] 安装 [[Paseo]] 时所依赖的 [[onnxruntime-node]] 报错，报错内容如下：
	- ```apl
	  sudo npm install -g @getpaseo/cli
	  npm warn deprecated @mariozechner/pi-agent-core@0.70.6: please use @earendil-works/pi-agent-core instead going forward
	  npm warn deprecated node-domexception@1.0.0: Use your platform's native DOMException instead
	  npm warn deprecated uuid@9.0.1: uuid@10 and below is no longer supported.  For ESM codebases, update to uuid@latest.  For CommonJS codebases, use uuid@11 (but be aware this version will likely be deprecated in 2028).
	  npm warn deprecated @mariozechner/pi-tui@0.70.6: please use @earendil-works/pi-tui instead going forward
	  npm warn deprecated @mariozechner/pi-ai@0.70.6: please use @earendil-works/pi-ai instead going forward
	  npm warn deprecated @mariozechner/pi-coding-agent@0.70.6: please use @earendil-works/pi-coding-agent instead going forward
	  npm error code 1
	  npm error path /usr/local/lib/node_modules/@getpaseo/cli/node_modules/onnxruntime-node
	  npm error command failed
	  npm error command sh -c node ./script/install
	  npm error /usr/local/lib/node_modules/@getpaseo/cli/node_modules/onnxruntime-node/script/install-utils.js:57
	  npm error           reject(new Error(`Failed to download build list. HTTP status code = ${statusCode}`));
	  npm error                  ^
	  npm error
	  npm error Error: Failed to download build list. HTTP status code = 302
	  npm error     at ClientRequest.<anonymous> (/usr/local/lib/node_modules/@getpaseo/cli/node_modules/onnxruntime-node/script/install-utils.js:57:18)
	  npm error     at Object.onceWrapper (node:events:623:26)
	  npm error     at ClientRequest.emit (node:events:508:28)
	  npm error     at HTTPParser.parserOnIncomingClient (node:_http_client:780:27)
	  npm error     at HTTPParser.parserOnHeadersComplete (node:_http_common:125:17)
	  npm error     at TLSSocket.socketOnData (node:_http_client:615:22)
	  npm error     at TLSSocket.emit (node:events:508:28)
	  npm error     at addChunk (node:internal/streams/readable:563:12)
	  npm error     at readableAddChunkPushByteMode (node:internal/streams/readable:514:3)
	  npm error     at Readable.push (node:internal/streams/readable:394:5)
	  npm error
	  npm error Node.js v24.14.1
	  npm error A complete log of this run can be found in: /root/.npm/_logs/2026-05-11T02_19_10_946Z-debug-0.log
	  ```
- # 解决方案
	- > 根据 [[Kimi]] 的回答内容收集整理
	- 使用 `--ignore-scripts` 跳过安装脚本
		- ```
		  sudo npm install -g @getpaseo/cli --ignore-scripts
		  ```
	- 然后手动下载 ONNX Runtime：
		- ```
		  cd /usr/local/lib/node_modules/@getpaseo/cli/node_modules/onnxruntime-node
		  ```
	- 查看需要的版本
		- ```
		  cat package.json | grep version
		  ```
	- 手动下载对应平台的二进制（以 x64 Linux 为例）
	- ```sudo curl -L -o onnxruntime-linux-x64-1.17.1.tgz \
	  https://github.com/microsoft/onnxruntime/releases/download/v<version>/onnxruntime-linux-x64-<version>.tgz
	  
	  sudo tar -xzf onnxruntime-linux-x64-<version>.tgz
	  sudo mkdir -p bin
	  sudo cp onnxruntime-linux-x64-<version>/lib/libonnxruntime.so* bin/
	  sudo rm -rf onnxruntime-linux-x64-<version> onnxruntime-linux-x64-<version>.tgz
	  ```
		- > `<version>`: 替换为对应版本