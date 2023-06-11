# Install NVIDIA [k8s-device-plugin](https://github.com/NVIDIA/k8s-device-plugin) with CRI-O

Install `nvidia-driver`, `nvidia-container-toolkit`, and `cuda`.

TODO: document repo installation.

Create `/usr/share/containers/oci/hooks.d/oci-nvidia-hook.json`:

```
cat > /usr/share/containers/oci/hooks.d/oci-nvidia-hook.json << EOF
{
    "version": "1.0.0",
    "hook": {
        "path": "/usr/bin/nvidia-container-toolkit",
        "args": ["nvidia-container-toolkit", "prestart"]
    },
    "when": {
        "always": true,
        "commands": [".*"]
    },
    "stages": ["prestart"]
}
EOF
```
