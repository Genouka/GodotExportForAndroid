# GodotExportForAndroid
2024-07-06 更改一些文字说明

2024-04-26 修正一些文字说明

2024-02-24 修复解压的一些bug

Android版本Godot使用Github CI导出Godot项目的完整解决方案。

> [!NOTE]
> 你可以直接使用GodotHelper（在qq群517549773中小范围测试）完成这些操作。但其是闭源软件哦。（开发者：Genouka）
>
> 也可以试试支持在手机上离线导出的[Godot导出助手（闭源软件）](https://gdh.genouka.rr.nu/)

Bilibili:Genouka

**只有[github.com/Genouka/GodotExportForAndroid](https://github.com/Genouka/GodotExportForAndroid)是官方仓库，不要fork别人fork的仓库。**


## 通用步骤：
### 0.注意事项
本仓库使用的是Godot Linux 4.1.1版本（非mono），以后再支持更多版本。

**如果有问题请sync（同步）你的仓库至与上游仓库（也就是我的仓库）的最新版本。**

> [!TIP]
> 如果在操作过程中有任何问题，请提交issue或者加入qq群：517549773

### 1.为本仓库点个star
据说给个star可以让开发者更高效地产出！

### 2.fork本仓库
公有仓库足以满足要求。**因为放入和生成的文件是带密码的。**

> [!WARNING]
> 如果一定要改成私有仓库，可能会在你自己的账户下计费，那就与我无关了。

### 3.进Action选项卡，启用Action功能
这步要先做，不然设置找不到secert选项
### 4.添加secert
打开`仓库设置>Security>Secrets and variables>Actions`。

然后点`New repository secret`按钮

名称填`GDC_PASSWORD`

内容填你之后要设置的src.zip文件的密码（这个密码也是你取回时候用的密码）

> [!WARNING]
> 已知问题：密码不可以带空格和shell脚本关键字符号，否则会导致导出出现错误！
> 如果你不知道该怎么做，让密码只包含数字和大小写字母就行了。

记得点保存！

### 5.配置并上传

#### 5.1.配置工程的导出

修改`export_presets.cfg`。

> [!TIP]
> 建议直接在Godot内修改导出配置哦，会自动在项目路径下生成该文件。

添加几个平台配置就会相应导出几个，记得要填导出的文件名（建议不要填绝对路径，填`./output.apk`，其他的未经过测试）。

以下是一份导出三个平台的`export_presets.cfg`配置示例

> [!WARNING]
> 本示例**没有**为Android添加签名，如需用于生产环境请先配置签名。

<details>
<summary>展开查看示例</summary>
<pre><code>
[preset.0]

name="Android"
platform="Android"
runnable=true
dedicated_server=false
custom_features=""
export_filter="all_resources"
include_filter=""
exclude_filter=""
export_path="./something.apk"
encryption_include_filters=""
encryption_exclude_filters=""
encrypt_pck=false
encrypt_directory=false

[preset.0.options]

custom_template/debug=""
custom_template/release=""
gradle_build/use_gradle_build=false
gradle_build/export_format=0
gradle_build/min_sdk=""
gradle_build/target_sdk=""
architectures/armeabi-v7a=false
architectures/arm64-v8a=true
architectures/x86=false
architectures/x86_64=false
version/code=1
version/name=""
package/unique_name="org.godotengine.gennme"
package/name=""
package/signed=false
package/app_category=2
package/retain_data_on_uninstall=false
package/exclude_from_recents=false
package/show_in_android_tv=false
package/show_as_launcher_app=false
launcher_icons/main_192x192=""
launcher_icons/adaptive_foreground_432x432=""
launcher_icons/adaptive_background_432x432=""
graphics/opengl_debug=false
xr_features/xr_mode=0
screen/immersive_mode=true
screen/support_small=true
screen/support_normal=true
screen/support_large=true
screen/support_xlarge=true
user_data_backup/allow=false
command_line/extra_args=""
apk_expansion/enable=false
apk_expansion/SALT=""
apk_expansion/public_key=""
permissions/custom_permissions=PackedStringArray()
permissions/access_checkin_properties=false
permissions/access_coarse_location=false
permissions/access_fine_location=false
permissions/access_location_extra_commands=false
permissions/access_mock_location=false
permissions/access_network_state=false
permissions/access_surface_flinger=false
permissions/access_wifi_state=false
permissions/account_manager=false
permissions/add_voicemail=false
permissions/authenticate_accounts=false
permissions/battery_stats=false
permissions/bind_accessibility_service=false
permissions/bind_appwidget=false
permissions/bind_device_admin=false
permissions/bind_input_method=false
permissions/bind_nfc_service=false
permissions/bind_notification_listener_service=false
permissions/bind_print_service=false
permissions/bind_remoteviews=false
permissions/bind_text_service=false
permissions/bind_vpn_service=false
permissions/bind_wallpaper=false
permissions/bluetooth=false
permissions/bluetooth_admin=false
permissions/bluetooth_privileged=false
permissions/brick=false
permissions/broadcast_package_removed=false
permissions/broadcast_sms=false
permissions/broadcast_sticky=false
permissions/broadcast_wap_push=false
permissions/call_phone=false
permissions/call_privileged=false
permissions/camera=false
permissions/capture_audio_output=false
permissions/capture_secure_video_output=false
permissions/capture_video_output=false
permissions/change_component_enabled_state=false
permissions/change_configuration=false
permissions/change_network_state=false
permissions/change_wifi_multicast_state=false
permissions/change_wifi_state=false
permissions/clear_app_cache=false
permissions/clear_app_user_data=false
permissions/control_location_updates=false
permissions/delete_cache_files=false
permissions/delete_packages=false
permissions/device_power=false
permissions/diagnostic=false
permissions/disable_keyguard=false
permissions/dump=false
permissions/expand_status_bar=false
permissions/factory_test=false
permissions/flashlight=false
permissions/force_back=false
permissions/get_accounts=false
permissions/get_package_size=false
permissions/get_tasks=false
permissions/get_top_activity_info=false
permissions/global_search=false
permissions/hardware_test=false
permissions/inject_events=false
permissions/install_location_provider=false
permissions/install_packages=false
permissions/install_shortcut=false
permissions/internal_system_window=false
permissions/internet=false
permissions/kill_background_processes=false
permissions/location_hardware=false
permissions/manage_accounts=false
permissions/manage_app_tokens=false
permissions/manage_documents=false
permissions/manage_external_storage=false
permissions/master_clear=false
permissions/media_content_control=false
permissions/modify_audio_settings=false
permissions/modify_phone_state=false
permissions/mount_format_filesystems=false
permissions/mount_unmount_filesystems=false
permissions/nfc=false
permissions/persistent_activity=false
permissions/process_outgoing_calls=false
permissions/read_calendar=false
permissions/read_call_log=false
permissions/read_contacts=false
permissions/read_external_storage=false
permissions/read_frame_buffer=false
permissions/read_history_bookmarks=false
permissions/read_input_state=false
permissions/read_logs=false
permissions/read_phone_state=false
permissions/read_profile=false
permissions/read_sms=false
permissions/read_social_stream=false
permissions/read_sync_settings=false
permissions/read_sync_stats=false
permissions/read_user_dictionary=false
permissions/reboot=false
permissions/receive_boot_completed=false
permissions/receive_mms=false
permissions/receive_sms=false
permissions/receive_wap_push=false
permissions/record_audio=false
permissions/reorder_tasks=false
permissions/restart_packages=false
permissions/send_respond_via_message=false
permissions/send_sms=false
permissions/set_activity_watcher=false
permissions/set_alarm=false
permissions/set_always_finish=false
permissions/set_animation_scale=false
permissions/set_debug_app=false
permissions/set_orientation=false
permissions/set_pointer_speed=false
permissions/set_preferred_applications=false
permissions/set_process_limit=false
permissions/set_time=false
permissions/set_time_zone=false
permissions/set_wallpaper=false
permissions/set_wallpaper_hints=false
permissions/signal_persistent_processes=false
permissions/status_bar=false
permissions/subscribed_feeds_read=false
permissions/subscribed_feeds_write=false
permissions/system_alert_window=false
permissions/transmit_ir=false
permissions/uninstall_shortcut=false
permissions/update_device_stats=false
permissions/use_credentials=false
permissions/use_sip=false
permissions/vibrate=false
permissions/wake_lock=false
permissions/write_apn_settings=false
permissions/write_calendar=false
permissions/write_call_log=false
permissions/write_contacts=false
permissions/write_external_storage=false
permissions/write_gservices=false
permissions/write_history_bookmarks=false
permissions/write_profile=false
permissions/write_secure_settings=false
permissions/write_settings=false
permissions/write_sms=false
permissions/write_social_stream=false
permissions/write_sync_settings=false
permissions/write_user_dictionary=false

[preset.1]

name="Linux/X11"
platform="Linux/X11"
runnable=true
dedicated_server=false
custom_features=""
export_filter="all_resources"
include_filter=""
exclude_filter=""
export_path="./linux_x11"
encryption_include_filters=""
encryption_exclude_filters=""
encrypt_pck=false
encrypt_directory=false

[preset.1.options]

custom_template/debug=""
custom_template/release=""
debug/export_console_wrapper=1
binary_format/embed_pck=false
texture_format/bptc=true
texture_format/s3tc=true
texture_format/etc=false
texture_format/etc2=false
binary_format/architecture="x86_64"
ssh_remote_deploy/enabled=false
ssh_remote_deploy/host="user@host_ip"
ssh_remote_deploy/port="22"
ssh_remote_deploy/extra_args_ssh=""
ssh_remote_deploy/extra_args_scp=""
ssh_remote_deploy/run_script="#!/usr/bin/env bash
export DISPLAY=:0
unzip -o -q \"{temp_dir}/{archive_name}\" -d \"{temp_dir}\"
\"{temp_dir}/{exe_name}\" {cmd_args}"
ssh_remote_deploy/cleanup_script="#!/usr/bin/env bash
kill $(pgrep -x -f \"{temp_dir}/{exe_name} {cmd_args}\")
rm -rf \"{temp_dir}\""

[preset.2]

name="Web"
platform="Web"
runnable=true
dedicated_server=false
custom_features=""
export_filter="all_resources"
include_filter=""
exclude_filter=""
export_path="./web.html"
encryption_include_filters=""
encryption_exclude_filters=""
encrypt_pck=false
encrypt_directory=false

[preset.2.options]

custom_template/debug=""
custom_template/release=""
variant/extensions_support=false
vram_texture_compression/for_desktop=true
vram_texture_compression/for_mobile=false
html/export_icon=true
html/custom_html_shell=""
html/head_include=""
html/canvas_resize_policy=2
html/focus_canvas_on_start=true
html/experimental_virtual_keyboard=false
progressive_web_app/enabled=false
progressive_web_app/offline_page=""
progressive_web_app/display=1
progressive_web_app/orientation=0
progressive_web_app/icon_144x144=""
progressive_web_app/icon_180x180=""
progressive_web_app/icon_512x512=""
progressive_web_app/background_color=Color(0, 0, 0, 1)

[preset.3]

name="Windows Desktop"
platform="Windows Desktop"
runnable=true
dedicated_server=false
custom_features=""
export_filter="all_resources"
include_filter=""
exclude_filter=""
export_path="windows.exe"
encryption_include_filters=""
encryption_exclude_filters=""
encrypt_pck=false
encrypt_directory=false

[preset.3.options]

custom_template/debug=""
custom_template/release=""
debug/export_console_wrapper=1
binary_format/embed_pck=false
texture_format/bptc=true
texture_format/s3tc=true
texture_format/etc=false
texture_format/etc2=false
binary_format/architecture="x86_64"
codesign/enable=false
codesign/timestamp=true
codesign/timestamp_server_url=""
codesign/digest_algorithm=1
codesign/description=""
codesign/custom_options=PackedStringArray()
application/modify_resources=true
application/icon=""
application/console_wrapper_icon=""
application/icon_interpolation=4
application/file_version=""
application/product_version=""
application/company_name=""
application/product_name=""
application/file_description=""
application/copyright=""
application/trademarks=""
ssh_remote_deploy/enabled=false
ssh_remote_deploy/host="user@host_ip"
ssh_remote_deploy/port="22"
ssh_remote_deploy/extra_args_ssh=""
ssh_remote_deploy/extra_args_scp=""
ssh_remote_deploy/run_script="Expand-Archive -LiteralPath '{temp_dir}\\{archive_name}' -DestinationPath '{temp_dir}'
$action = New-ScheduledTaskAction -Execute '{temp_dir}\\{exe_name}' -Argument '{cmd_args}'
$trigger = New-ScheduledTaskTrigger -Once -At 00:00
$settings = New-ScheduledTaskSettingsSet
$task = New-ScheduledTask -Action $action -Trigger $trigger -Settings $settings
Register-ScheduledTask godot_remote_debug -InputObject $task -Force:$true
Start-ScheduledTask -TaskName godot_remote_debug
while (Get-ScheduledTask -TaskName godot_remote_debug | ? State -eq running) { Start-Sleep -Milliseconds 100 }
Unregister-ScheduledTask -TaskName godot_remote_debug -Confirm:$false -ErrorAction:SilentlyContinue"
ssh_remote_deploy/cleanup_script="Stop-ScheduledTask -TaskName godot_remote_debug -ErrorAction:SilentlyContinue
Unregister-ScheduledTask -TaskName godot_remote_debug -Confirm:$false -ErrorAction:SilentlyContinue
Remove-Item -Recurse -Force '{temp_dir}'"
</code></pre>
</details>

#### 5.2.上传

带密码压缩你的整个项目。

> [!WARNING]
> 已知问题：如果你的项目包含LICENSE或README.md文件，请删除或重命名它们再上传，否则运行Action时会出现覆盖失败的问题。

上传的文件名为`src.zip`，放仓库main分支根目录就行了。

如果仓库已经有这个文件请先删了。

注意：请带密码压缩，密码就是你之前设置的。

注：目前代码使用7z解压缩和压缩，效果已经很好了，unzip已经测试过了用不了，已经移除对应代码了。

### 6.运行Action
在Github的仓库页面进入`Action`选项卡，点上面`All workflows`（右边带个向下的箭头）那个东西，选`cloudbuild`，这时可以看到页面上有个蓝色的横幅：

```
This workflow has a workflow_dispatch event trigger.
```

点横幅右侧的`Run workflow`，选`main`分支就行了。

> [!NOTE]
> 如果你把文件传的是别的分支就选对应分支，一般就是`main`分支。

显示成功的横幅后需要刷新一下页面，不然不显示构建进度（Github的小bug）

### 7.耐心等待
经过实际测试，本Action运行时长在1min30s到3min之间（不含等待时长），如果你的项目很大，可能需要的时间更长。

### 8.下载文件
点开最新的Action构建任务，如果构建完成，下方会出现一个名为dest.zip的Artifacts，点击下载（根据你导出的平台的数量，文件可能较大）

**里面嵌套的压缩文件`dest.zip`的密码为你之前设置的那个密码。**

> [!NOTE]
> 我没有你设置的密码，不要找我要，你找我要也没有，因为是你自己设置的。

## Q&A
### q1.我下次还想用还要这么麻烦吗？
不用这么麻烦，只要重复步骤5、6、7、8即可

### q2.密码泄露了怎么办
删掉以往提交的含有泄露密码的压缩文件的commit，然后进Action，把之前的泄露密码的Artifacts删了，最后换个密码（改secert，可以参照步骤4）

> [!TIP]
> 当然建议直接删库重新fork一个，更彻底也更快。

### q3.用你的仓库处理我的项目安全吗
相对安全。

开发者不收集也不能收集（只要你按上面步骤来，配置对了）任何信息，其他人也没有办法看到你的数据（除非你密码泄露了），取决于你信不信任微软了。

### q4.版权问题？
没有问题，Godot是MIT协议，本仓库为Apache-2.0 license协议，你想用拿去便是了，无需经过额外的同意。

> [!NOTE]
> 虽然如此，但是开发者还是希望你可以你可以将本仓库链接及作者署名在显眼的地方，这样我会很高兴的。

### q5.那个那个这个这个怎么办
有任何问题提交issues或者加入qq群517549773询问（我平时上学可能不在就是了，不过看到一定回）
