## multidisabler for Samsung Galaxy A73

Enables write access to / (system partition), /product and /vendor, converts / (system) file system to ext4
(otherwise you may hit a bootloop after modifying / because f2fs refuses to mount r/o with dirty journal),
disables encryption of /data, disables stock recovery restoration and disables other Samsung lockup
anti-features usually disabled by other multidisablers: Vaultkeeper, proca, TLC HDM/ICCC/KG, CASS, WSM, FRP.

Instructions:

- Unlock bootloader https://4pda.to/forum/index.php?showtopic=1058205
- Install TWRP
- Boot into recovery WITHOUT first rebooting to system, otherwise the stock firmware will remove TWRP and restore stock Recovery.
  To do it, reboot the phone with a connected USB cable and volume up and power keys pressed right after Download Mode.
- IF TWRP doesn't mount your /data (if you don't see your files from the internal flash) - wipe data partition: Wipe > Format Data
- Then EITHER take [multidisabler-a73-v5.zip](multidisabler-a73-v5.zip) (it just contains the [multidisabler](multidisabler) script as `META-INF/com/google/android/update-binary`), copy it to TWRP and install it
- OR copy [multidisabler](multidisabler) to TWRP and just run it in the console. You can use TWRP's terminal or even adb shell to TWRP from your PC:
  ```
  adb push multidisabler /tmp/
  adb shell
  sh /tmp/multidisabler
  ```
- IF you didn't wipe data at the step 4, then wipe it: Wipe > Format Data
- Reboot into system
- If something goes wrong you can restore TWRP backup or just flash with Odin (or Heimdall in Linux: https://git.sr.ht/~grimler/Heimdall)
- After that you'll be able to remount FS to R/W with `mount -o remount,rw /` (or /vendor, /product) under root.

Checked and works in Android 12. Should also work in Android 13 firmware, but some users hit a bootloop after
doing modifications. Maybe Samsung invented another lockup feature in Android 13 firmware. It should be rather
easy to find and kill but this needs some testing. If you want to test it you can try and then, if you hit a
bootloop, you should copy `/proc/last_kmsg` from TWRP after an unsuccessful boot PLUS collect `adb logcat`
during boot and send both to me (@vitalif in telegram).

Git mirrors: https://yourcmc.ru/git/vitalif/multidisabler-a73 and https://github.com/vitalif/multidisabler-a73

## multidisabler для Samsung Galaxy A73

Активирует возможность записи в / (раздел system), /product и /vendor, конвертирует файловую систему
раздела / (system) в ext4 (иначе после модификаций можно попасть на бесконечную перезагрузку, так как
f2fs отказывается монтироваться в R/O с грязным журналом), отключает шифрование /data, отключает
восстановление штатного самсунговского recovery и отключает остальные самсунговские анти-функции
блокировок, которые обычно отключают multidisabler-ы: Vaultkeeper, proca, TLC HDM/ICCC/KG, CASS, WSM, FRP.

Инструкция:

- Разблокировать загрузчик https://4pda.to/forum/index.php?showtopic=1058205
- Установить TWRP
- НЕ перезагружаясь в систему, загрузиться в TWRP, иначе самсунг удалит TWRP и восстановит штатное Recovery. Для этого после Download Mode надо перезагрузиться с подключённым к компу USB проводом и зажатыми кнопками громкости вверх и включения
- ЕСЛИ раздел /data не примонтирован (вы не видите файлы из внутренней памяти) - очистить раздел данных: Wipe > Format Data
- Далее ЛИБО взять zip файл, содержащий данный скрипт как файл `META-INF/com/google/android/update-binary`, скопировать его в TWRP и установить (Install)
- ЛИБО скопировать данный скрипт в TWRP и запустить. Либо в терминале в TWRP, либо прямо в adb shell-консоли (при загруженном TWRP) с компа:
  ```
  adb push multidisabler /tmp/
  adb shell
  sh /tmp/multidisabler
  ```
- Если не чистили на шаге 4, то очистить раздел данных: Wipe > Format Data
- Перезагрузиться в систему
- Если что-то пошло не так, всегда можно восстановить бэкап TWRP или просто обычной прошивкой через один (или через Heimdall в Linux: https://git.sr.ht/~grimler/Heimdall)
- После этого перемонтировать ФС в r/w - из-под рута `mount -o remount,rw /` или соответственно `mount -o remount,rw /vendor`

Проверено и работает на прошивке Android 12. На 13 тоже должно работать, но некоторые пользователи
сталкивались с бесконечной перезагрузкой после фактического внесения изменения в систему. Возможно, Samsung
изобрёл очередную залочку в Android 13. Если вы хотите потестировать - попробуйте, а потом, если столкнётесь
с бесконечной перезагрузкой - скопируйте `/proc/last_kmsg` из TWRP после неудачной загрузки на компьютер, а
также соберите `adb logcat` В ПРОЦЕССЕ неудачной загрузки и отправьте оба вида логов мне (@vitalif в телеграме).

Git зеркала https://yourcmc.ru/git/vitalif/multidisabler-a73 и https://github.com/vitalif/multidisabler-a73
