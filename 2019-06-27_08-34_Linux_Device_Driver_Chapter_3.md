---
tags: Chapter 3, LinuxDeviceDriver
---

#Chapter 3 - Character Device Drivers

###Major and Minor Numbers
- Char devices filesystem içinde isimleri ile erişilebilir.
- Bunlar sistemde device files olarak geçer ve /dev klasörü içinde bulunurlar.
- ls -l komutu girildiğinde ilk column'unda c yazan devicelar char device olarak geçerler.
- Burada aynı zamanda block devices'lar da bulunur ve bunların başında b yazar.

crw--w----  1 root tty       4,  30 Jun 26 09:55 tty30
crw--w----  1 root tty       4,  31 Jun 26 09:55 tty31
crw--w----  1 root tty       4,  32 Jun 26 09:55 tty32
crw--w----  1 root tty       4,  33 Jun 26 09:55 tty33
crw--w----  1 root tty       4,  34 Jun 26 09:55 tty34
crw--w----  1 root tty       4,  35 Jun 26 09:55 tty35
crw--w----  1 root tty       4,  36 Jun 26 09:55 tty36
crw--w----  1 root tty       4,  37 Jun 26 09:55 tty37
crw--w----  1 root tty       4,  38 Jun 26 09:55 tty38
crw--w----  1 root tty       4,  39 Jun 26 09:55 tty39

- Major number tty yazılarından hemen sonraki sayıdır ve hangi driver'ın cihazların kontrolü için kullanıldığını belirtir. Minor numara ise tam olarak hangi cihazın bu driver'ı kullandığını belirtir. Mesela yukardaki durumda tüm tty cihazları 4 numaralı driver tarafından kontrol edilirken, yanındaki numaralar ise tam olarak hangi cihazın kontrol edildiğini belirtir.

- Kernelde dev_t tipi major ve minor sayıları tutmak için kullanılır. Bu major ve minor sayıları elde etmek için makrolar kullanırız.

´´´
MAJOR(dev_t dev);
MINOR(dev_t dev);

´´´
- Eğer major ve minor sayılara sahipsek ve bunu dev_t kullansın istiyorsak

´´´
MKDEV(int major, int minor);

´´´




