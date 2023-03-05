## multidisabler для Samsung Galaxy A73

Активирует возможность записи в / (раздел system) и /vendor, отключает шифрование /data, отключает восстановление самсунговского recovery

Инструкция

- Разблокировать загрузчик https://4pda.to/forum/index.php?showtopic=1058205
- Установить TWRP
- НЕ перезагружаясь в систему, загрузиться в TWRP, иначе самсунг удалит TWRP и восстановит штатное Recovery. Для этого после Download Mode надо перезагрузиться с подключённым к компу USB проводом и зажатыми кнопками громкости вверх и включения
- Далее ЛИБО взять zip файл, содержащий данный скрипт как файл `META-INF/com/google/android/update-binary`, скопировать его в TWRP и установить (Install)
- ЛИБО скопировать данный скрипт в TWRP и запустить. Либо в терминале в TWRP, либо прямо в adb shell-консоли (при загруженном TWRP) с компа:
  ```
  adb push multidisabler /tmp/
  adb shell
  sh /tmp/multidisabler
  ```
- Очистить раздел данных: в TWRP - Wipe > Format Data и перезагрузиться в систему
- Если что-то пошло не так, всегда можно восстановиться обычной прошивкой через один (или через Heimdall в Linux: https://git.sr.ht/~grimler/Heimdall)
- После этого перемонтировать ФС в r/w - из-под рута `mount -o remount,rw /` или соответственно `mount -o remount,rw /vendor`

Проверено на прошивке Android 12, на 13 ещё не проверено.

Git зеркала https://yourcmc.ru/git/vitalif/multidisabler-a73 и https://github.com/vitalif/multidisabler-a73
