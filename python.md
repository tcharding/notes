Python notes
============

list locally installed modules
------------------------------
import pip
installed_packages = pip.get_installed_distributions()
installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
for i in installed_packages])
print(installed_packages_list)

profile python script
---------------------
python -m cprofilev /path/to/script

http server
-----------
python -m http.server
