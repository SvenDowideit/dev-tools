This context exposes ports for agent deployment


### Usage

1. Update the `hostPath` property in all `configs/**/kind.yaml` files to match the path of the project on your filesystem
2. (optional) Update the `hostPort` property in all `configs/**/kind.yaml` files to the port that suits you the best to access portainer instance. Default ports (http, https) are, by context:
  * agent: 9050, 9051, 
3. Create the cluster with `./setup.sh create <ENV>` where `<ENV>` is the name of the subfolder inside `configs` folder
4. Start Portainer in development mode via `yarn start`
5. Build the agent `./dev.sh build`
6. `kubectl --context kind-agent apply -f  ./configs/agent/portainer.yaml -f ./configs/agent/agent.yaml`

Open browser at `localhost:<hostPort>` (`hostPort` is defined in `kind.yaml` file, default values listed above)

Then add the endpoint - you can use <your host's IP, not localhost/127.0.0.x>:30778 for the agent URL
