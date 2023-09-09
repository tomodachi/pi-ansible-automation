configuring the sender to stream to the roc-sink

on your workstation (sender)
~/.config/pipewire/pipewire.conf.d/pipewire.conf

context.modules = [
  {   name = libpipewire-module-roc-sink
      args = {
          fec.code = rs8m
          remote.ip = ip-of-device-with-roc-sink
          remote.source.port = 10001
          remote.repair.port = 10002
          sink.name = "Roc Sink livingroom"
          sink.props = {
             node.name = "roc-sink-livingroom"
          }
      }
  }
]

and restart pipewire and you should see a new output ready to receive audio
