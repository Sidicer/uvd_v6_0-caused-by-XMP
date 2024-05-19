# uvd_v6_0 is caused by XMP
> `[drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!` is caused by X.M.P

<sub>not 100% as it can also be caused by `Legacy` (BIOS) boot option, but that was discussed plenty in other threads</sub>

---

After a full day of troubleshooting and re-flashing multiple bios'es for my RX570 *(Polaris10)* I accidentally disabled XMP profile in the BIOS settings and `amdgpu` successfully loaded.

### XMP ON
```log
...skipping...
kernel: [drm] add ip block number 7 <uvd_v6_0>
...skipping...
kernel: snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, trying to reset the VCPU!!!
kernel: [drm:uvd_v6_0_start [amdgpu]] *ERROR* UVD not responding, giving up!!!
kernel: [drm:amdgpu_device_ip_set_powergating_state [amdgpu]] *ERROR* set_powergating_state of IP block <uvd_v6_0> failed -1
kernel: amdgpu 0000:01:00.0: [drm:amdgpu_ring_test_helper [amdgpu]] *ERROR* ring uvd test failed (-110)
kernel: [drm:amdgpu_device_init.cold [amdgpu]] *ERROR* hw_init of IP block <uvd_v6_0> failed -110
kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu_device_ip_init failed
kernel: amdgpu 0000:01:00.0: amdgpu: Fatal error during GPU init
kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu: finishing device.
```
### XMP OFF
```log
...skipping...
kernel: [drm] add ip block number 7 <uvd_v6_0>
...skipping...
kernel: snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops amdgpu_dm_audio_component_bind_ops [>
kernel: [drm] UVD and UVD ENC initialized successfully.
kernel: [drm] VCE initialized successfully.
kernel:kfdkfd: amdgpu: Allocated 3969056 bytes on gart
kernel:kfdkfd: amdgpu: Total number ofkFD nodes to be created: 1
kernel: amdgpu: Virtual CRAT table created for GPU
kernel: amdgpu: Topology: Add dGPU node [0x67df:0x1002]
kernel:kfdkfd: amdgpu: added device 1002:67df
kernel: amdgpu 0000:01:00.0: amdgpu: SE 4, SH per SE 1, CU per SH 9, active_cu_number 32
kernel: amdgpu 0000:01:00.0: amdgpu: Using BOCO for runtime pm
kernel: [drm] Initialized amdgpu 3.57.0 20150101 for 0000:01:00.0 on minor 1
kernel: fbcon: amdgpudrmfb (fb0) is primary device
kernel: Console: switching to colour frame buffer device 215x45
kernel: amdgpu 0000:01:00.0: [drm] fb0: amdgpudrmfb frame buffer device
```

*full boot logs added to the repo*

---

Setup:
```
- Asus Z97-AR (Motherboard) BIOS Ver. 3503
- intel i5-4690 @ 3.50GHz
- Mismatched Ram (Corsair 4GB 1333MHz x2 + Kingston 4GB 1600MHz x2)
- XMP timing: ddr3-1600 9-9-9-24-2N-1.50V
- UEFI Only boot
```
