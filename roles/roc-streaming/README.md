# roc-streaming 

## Real-time audio streaming over the network

## Local configuration:
On your workstation (sender) to the following file:
~/.config/pipewire/pipewire.conf.d/pipewire.conf
add

```
context.modules = [
  {   name = libpipewire-module-roc-sink
      args = {
          fec.code = rs8m
          remote.ip = 10.0.5.39
          remote.source.port = 10001
          remote.repair.port = 10002
          remote_control_port= 10003
          sink.name = "Roc Sink"
          sink.props = {
             node.name = "roc-sink"
          }
      }
  }
]
```

Restart pipewire (systemctl --user restart pipewire) and you should see a new output ready to receive audio
