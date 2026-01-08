EDID Repository
===============

This is a repository of decoded EDIDs from various digital and analog monitors collected
by Linux users at https://linux-hardware.org.

Everyone can contribute to this repository by uploading probes of their computers
by the [hw-probe](https://github.com/linuxhw/hw-probe) tool:

    sudo -E hw-probe -all -upload

EDIDs of all connected monitors will be uploaded to the database and repository.

TIP: discuss your monitors and EDIDs on [our forum](https://forum.linux-hardware.org/)

Total monitors: 174781.

Contents
--------

1. [ About ](#about)
2. [ How to install EDID file ](#how-to-install-edid-file)
3. [ How to regenerate data ](#how-to-regenerate-data)
4. [ Digital display ](#digital-display)
5. [ Analog display  ](#analog-display)

About
-----

The structure of the repository is the following:

    {TYPE}/{VENDOR}/{MODEL}/{ID}

    ( e.g. Digital/LG Display/LGD0217/925C880E8A08 )

ID of a monitor is MD5 of EDID.

How to install EDID file
------------------------

Generate binary EDID file:

    cat EDID.txt | grep -E '^([a-f0-9]{32}|[a-f0-9 ]{47})$' | tr -d '[:space:]' | xxd -r -p > EDID.bin

Verify it by `edid-decode`:

    edid-decode EDID.bin

Install `EDID.bin` by [write-edid](https://github.com/linuxhw/write-edid) or [edid-rw](https://github.com/bulletmark/edid-rw).

How to regenerate data
----------------------

Regenerate all the data by new edid-decode:

    find . -type f -regextype posix-extended -regex '.*/[A-F0-9]{12}$' -print0 | while read -r -d '' file; do cat "$file" | grep -E '^([a-f0-9]{32}|[a-f0-9 ]{47})$' | edid-decode-2023-05-07 -c --skip-sha > /tmp/file; cat /tmp/file > "$file"; done
    find . -type f -regextype posix-extended -regex '.*/[A-F0-9]{12}$' -print0 | while read -r -d '' file; do sed -i -e "s/Serial Number: .*/Serial Number: .../g" "$file"; done

Digital display
---------------

You can find decoded EDIDs for listed monitors in the repository by vendor name,
model and ID.

| MFG              | Model   | Name             | Res       | Inch | Made | ID |
|------------------|---------|------------------|-----------|------|------|----|
| ADI              | ADI217A | MS A715          | 1280x1024 | 16.8 | 2003 | [C7D9F20713AC](<Digital/ADI/ADI217A/C7D9F20713AC>) |
| ADI              | ADI217D | MS A715          | 1280x1024 | 16.8 |      | [512AC71EBDE1](<Digital/ADI/ADI217D/512AC71EBDE1>) |
| ADI              | ADI2930 |                  | 1280x1024 | 17.1 |      | [4674250BE90C](<Digital/ADI/ADI2930/4674250BE90C>) |
| AG Neovo         | AGN1624 | L-W24C           | 1920x1080 | 23.6 | 2016 | [9627AC498D46](<Digital/AG Neovo/AGN1624/9627AC498D46>) |
| AG Neovo         | AGN6020 | LW-22E           | 1920x1080 | 21.7 | 2019 | [3752F2688147](<Digital/AG Neovo/AGN6020/3752F2688147>) |
| AG Neovo         | AGN9505 | LA-2702          | 1920x1080 | 27.0 | 2022 | [CF5C1EF393F0](<Digital/AG Neovo/AGN9505/CF5C1EF393F0>) |
| ALPD             | APO0030 | Pico-2           | 3840x2160 | 52.0 | 2016 | [85F22D1B9AB3](<Digital/ALPD/APO0030/85F22D1B9AB3>) |
| ALPD             | APO0808 | A210316PM3Q      | 1920x1080 | 15.6 | 2021 | [BBC19C7BC417](<Digital/ALPD/APO0808/BBC19C7BC417>) |
| AMH              | AMH0000 | A399U            | 3840x2160 | 40.0 | 2015 | [22ECE56F263D](<Digital/AMH/AMH0000/22ECE56F263D>) |
| AMT              | AMT0000 | HDMI             | 1600x900  | 19.9 | 2016 | [CA3069E95545](<Digital/AMT/AMT0000/CA3069E95545>) |
| AMT              | AMT0038 | L2-150T+         | 1024x768  | 14.9 | 2002 | [359C20500A6A](<Digital/AMT/AMT0038/359C20500A6A>) |
| AMT              | AMT3200 | AN-320W01D       | 1920x1080 | 32.0 | 2018 | [AD3CC3B9A2F2](<Digital/AMT/AMT3200/AD3CC3B9A2F2>) |
| AMT Internati... | AMT0038 | L2-150T+         | 1280x720  | 14.9 |      | [5C3934DAA3E1](<Digital/AMT International/AMT0038/5C3934DAA3E1>) |
| AMT Internati... | AMTA617 |                  | 1280x1024 | 17.1 |      | [FB83314D1480](<Digital/AMT International/AMTA617/FB83314D1480>) |
| AMW              | AMW0000 | X1700DS          | 1280x1024 | 17.1 | 2008 | [282733B186F2](<Digital/AMW/AMW0000/282733B186F2>) |
| AMW              | AMW0000 | X1900DS          | 1280x1024 | 18.8 | 2008 | [389207E25B70](<Digital/AMW/AMW0000/389207E25B70>) |
| AMW              | AMW0000 | A912WDB          | 1440x900  | 18.6 | 2007 | [3A103D89E198](<Digital/AMW/AMW0000/3A103D89E198>) |
| AMW              | AMW0000 | X1910WDS         | 1440x900  | 19.4 | 2007 | [8D2FFF12201B](<Digital/AMW/AMW0000/8D2FFF12201B>) |
| AMW              | AMW0000 | X2210WAS         | 1680x1050 | 22.3 | 2007 | [BA2843C47EF3](<Digital/AMW/AMW0000/BA2843C47EF3>) |
| AMW              | AMW1901 | M197TD           | 1280x1024 | 19.1 |      | [BD53E2980BD3](<Digital/AMW/AMW1901/BD53E2980BD3>) |
| AMW              | AMW73D7 | M179D            | 1280x1024 | 17.1 | 2005 | [4BBD8BD39675](<Digital/AMW/AMW73D7/4BBD8BD39675>) |
| AMW              | AMW73D7 | M179D            | 1280x1024 | 17.1 |      | [4D6D8877E4FC](<Digital/AMW/AMW73D7/4D6D8877E4FC>) |
| AOC              | AOC0000 | 43S5195          | 1920x1080 | 43.0 | 2020 | [34EDABC9923C](<Digital/AOC/AOC0000/34EDABC9923C>) |
| AOC              | AOC0000 | 32S5195          | 1920x1080 | 32.1 | 2020 | [B7CFC980F0C3](<Digital/AOC/AOC0000/B7CFC980F0C3>) |
| AOC              | AOC0000 | FTV              | 1920x1080 | 28.9 | 2019 | [132A50FA1C01](<Digital/AOC/AOC0000/132A50FA1C01>) |
| AOC              | AOC0000 | 43S5195          | 1920x1080 | 43.0 | 2019 | [25DAFB6ACD4C](<Digital/AOC/AOC0000/25DAFB6ACD4C>) |
| AOC              | AOC0000 | 32S5195          | 1920x1080 | 32.1 | 2019 | [283762764794](<Digital/AOC/AOC0000/283762764794>) |
| AOC              | AOC0000 | TV               | 1920x1080 | 65.0 | 2018 | [80F21BC4DD42](<Digital/AOC/AOC0000/80F21BC4DD42>) |
| AOC              | AOC0000 | TV               | 1920x1080 | 65.0 | 2017 | [6DD837FDBA1F](<Digital/AOC/AOC0000/6DD837FDBA1F>) |
| AOC              | AOC0000 | FTV              | 1920x1080 | 28.9 | 2016 | [3DEE98D30B2F](<Digital/AOC/AOC0000/3DEE98D30B2F>) |
| AOC              | AOC0000 | LCD              | 1360x768  | 23.4 | 2016 | [A46EA53CA45F](<Digital/AOC/AOC0000/A46EA53CA45F>) |
| AOC              | AOC0000 | LCD              | 1920x1080 | 40.2 | 2016 | [AC4090E2503A](<Digital/AOC/AOC0000/AC4090E2503A>) |
| AOC              | AOC0000 | LCD              | 1920x1080 | 40.2 | 2015 | [37E1CC9BD0E9](<Digital/AOC/AOC0000/37E1CC9BD0E9>) |
| AOC              | AOC0000 | LCD              | 1920x1080 | 40.2 | 2014 | [165C5B383B4E](<Digital/AOC/AOC0000/165C5B383B4E>) |
| AOC              | AOC0000 | LCD              | 1360x768  | 31.5 | 2014 | [4546A420D380](<Digital/AOC/AOC0000/4546A420D380>) |
| AOC              | AOC0000 | LCD              | 1360x768  | 23.4 | 2014 | [60E8C36C1790](<Digital/AOC/AOC0000/60E8C36C1790>) |
| AOC              | AOC0000 | LCD              | 1360x768  | 31.5 | 2013 | [0A098F71D0EB](<Digital/AOC/AOC0000/0A098F71D0EB>) |
| AOC              | AOC0000 | LCD              | 1920x1080 | 41.9 | 2013 | [3250F40FECD6](<Digital/AOC/AOC0000/3250F40FECD6>) |
| AOC              | AOC0000 | LCD              | 1360x768  | 41.9 | 2013 | [3DB80E127936](<Digital/AOC/AOC0000/3DB80E127936>) |
| AOC              | AOC0000 | FHD LCD          | 1920x1080 | 21.7 | 2013 | [4068AF502941](<Digital/AOC/AOC0000/4068AF502941>) |
| AOC              | AOC0000 | LCD              | 1920x1080 | 40.2 | 2013 | [4A699C476516](<Digital/AOC/AOC0000/4A699C476516>) |
| AOC              | AOC0000 | LCD              | 1920x1080 | 31.5 | 2013 | [CB042E4A5B33](<Digital/AOC/AOC0000/CB042E4A5B33>) |
| AOC              | AOC0000 | LCD              | 1360x768  | 30.9 | 2013 | [E33F3A727DC6](<Digital/AOC/AOC0000/E33F3A727DC6>) |
| AOC              | AOC0000 |                  | 3840x2160 | 65.0 |      | [DDAAC5BB78CD](<Digital/AOC/AOC0000/DDAAC5BB78CD>) |
| AOC              | AOC0000 |                  | 1920x1080 | 28.9 |      | [E590B5F28E7E](<Digital/AOC/AOC0000/E590B5F28E7E>) |
| AOC              | AOC0001 | G2460            | 1920x1080 | 24.0 | 2017 | [0BEFA0494CAD](<Digital/AOC/AOC0001/0BEFA0494CAD>) |
| AOC              | AOC0001 | 2460G4           | 1920x1080 | 24.0 | 2016 | [0817506D43D2](<Digital/AOC/AOC0001/0817506D43D2>) |
| AOC              | AOC0001 | 2460X            | 1920x1200 | 24.0 | 2016 | [C4EA3D9D1B90](<Digital/AOC/AOC0001/C4EA3D9D1B90>) |
| AOC              | AOC0001 | G2460            | 1920x1080 | 24.0 | 2015 | [0420EB9741E8](<Digital/AOC/AOC0001/0420EB9741E8>) |
| AOC              | AOC0001 | G2460            | 1920x1080 | 24.0 | 2014 | [050F7173A1EF](<Digital/AOC/AOC0001/050F7173A1EF>) |
| AOC              | AOC0001 | 2460X            | 1920x1200 | 24.0 | 2014 | [078D9DDF4612](<Digital/AOC/AOC0001/078D9DDF4612>) |
| AOC              | AOC0001 | 2460             | 1920x1080 | 24.0 | 2012 | [ABA107C0E9CF](<Digital/AOC/AOC0001/ABA107C0E9CF>) |
| AOC              | AOC0001 | G2460            | 1920x1080 | 24.0 |      | [047C5B2240A5](<Digital/AOC/AOC0001/047C5B2240A5>) |
| AOC              | AOC0CCD | Woieyeks-4K      | 2560x1440 | 27.8 | 2017 | [3870546A0869](<Digital/AOC/AOC0CCD/3870546A0869>) |
| AOC              | AOC0CCD | 28E850           | 2560x1600 | 27.8 | 2017 | [82A0A0F41AA1](<Digital/AOC/AOC0CCD/82A0A0F41AA1>) |
| AOC              | AOC0CCD | 28E850           | 1920x1080 | 27.8 | 2017 | [E52476ED7FEA](<Digital/AOC/AOC0CCD/E52476ED7FEA>) |
| AOC              | AOC1519 | 519W             | 1280x720  | 15.0 | 2008 | [5082AD989499](<Digital/AOC/AOC1519/5082AD989499>) |
| AOC              | AOC1560 | TFT1560          | 1024x768  | 14.9 | 2006 | [DC9E71EBEDA1](<Digital/AOC/AOC1560/DC9E71EBEDA1>) |
| AOC              | AOC1601 | 1601W            | 1920x1080 | 15.3 | 2022 | [B63C1FEBBD64](<Digital/AOC/AOC1601/B63C1FEBBD64>) |
| AOC              | AOC1601 | 1601W            | 1920x1080 | 15.3 | 2020 | [86BE1A68A859](<Digital/AOC/AOC1601/86BE1A68A859>) |
| AOC              | AOC1601 | 1601W            | 1920x1080 | 15.3 | 2019 | [5C4E23152864](<Digital/AOC/AOC1601/5C4E23152864>) |
| AOC              | AOC1610 | 16T10            | 1920x1080 | 15.3 | 2024 | [07FD65F9AD49](<Digital/AOC/AOC1610/07FD65F9AD49>) |
| AOC              | AOC1615 | 16T15            | 1920x1080 | 15.3 | 2024 | [102FDF7E7690](<Digital/AOC/AOC1615/102FDF7E7690>) |
| AOC              | AOC1619 | 1619w            | 1366x768  | 15.3 | 2009 | [3F5FD1D4692F](<Digital/AOC/AOC1619/3F5FD1D4692F>) |
| AOC              | AOC1619 | 1619w            | 1366x768  | 15.3 | 2008 | [93532CE869C0](<Digital/AOC/AOC1619/93532CE869C0>) |
| AOC              | AOC1620 | 1620             | 1366x768  | 15.3 | 2011 | [F6476C1DE90F](<Digital/AOC/AOC1620/F6476C1DE90F>) |
| AOC              | AOC1621 | 1621Wb           | 1366x768  | 15.3 | 2011 | [2C0FED7DF214](<Digital/AOC/AOC1621/2C0FED7DF214>) |
| AOC              | AOC1649 |                  | 1366x768  | 15.3 | 2015 | [A81949C9BEF0](<Digital/AOC/AOC1649/A81949C9BEF0>) |
| AOC              | AOC1649 | 1649W            | 1366x768  | 15.3 |      | [AF125DB56A36](<Digital/AOC/AOC1649/AF125DB56A36>) |
| AOC              | AOC1659 |                  | 1366x768  | 15.3 | 2015 | [5DC2A1AB22F5](<Digital/AOC/AOC1659/5DC2A1AB22F5>) |
| AOC              | AOC1659 |                  | 1920x1080 | 15.3 | 2013 | [5BF6396D5BB1](<Digital/AOC/AOC1659/5BF6396D5BB1>) |
| AOC              | AOC1670 | 1670W            | 1366x768  | 15.3 | 2017 | [1820E6BC1AAF](<Digital/AOC/AOC1670/1820E6BC1AAF>) |
| AOC              | AOC1670 | 1670W            | 1366x768  | 15.3 | 2016 | [459666340956](<Digital/AOC/AOC1670/459666340956>) |
| AOC              | AOC1670 | 1670W            | 1366x768  | 15.3 | 2015 | [134E66E5EE21](<Digital/AOC/AOC1670/134E66E5EE21>) |
| AOC              | AOC1670 | 1670W            | 1366x768  | 15.3 | 2014 | [74C3482C3808](<Digital/AOC/AOC1670/74C3482C3808>) |
| AOC              | AOC1712 | 712Sa            | 1280x1024 | 17.1 | 2008 | [D6554CF229E5](<Digital/AOC/AOC1712/D6554CF229E5>) |
| AOC              | AOC1712 | 712Sa            | 1280x1024 | 17.1 | 2007 | [9FD61637063C](<Digital/AOC/AOC1712/9FD61637063C>) |
| AOC              | AOC1716 | 716Sw            | 1280x720  | 17.1 | 2008 | [7803804C3686](<Digital/AOC/AOC1716/7803804C3686>) |
| AOC              | AOC1716 | 716Vwy           | 1440x900  | 17.2 | 2008 | [BC73640A56C8](<Digital/AOC/AOC1716/BC73640A56C8>) |
| AOC              | AOC1716 | 716Vwy           | 1440x900  | 17.2 | 2007 | [455D517C6221](<Digital/AOC/AOC1716/455D517C6221>) |
| AOC              | AOC1717 | 717wx            | 1440x900  | 17.2 | 2009 | [748B0B0516E7](<Digital/AOC/AOC1717/748B0B0516E7>) |
| AOC              | AOC1717 | 717wx            | 1440x900  | 17.2 | 2008 | [D2B26717F819](<Digital/AOC/AOC1717/D2B26717F819>) |
| AOC              | AOC1717 | 717wx            | 1440x900  | 17.2 |      | [0A105713B269](<Digital/AOC/AOC1717/0A105713B269>) |
| AOC              | AOC1719 | 1719             | 1280x1024 | 17.1 | 2014 | [DDF11C7CC624](<Digital/AOC/AOC1719/DDF11C7CC624>) |
| AOC              | AOC1719 | 1719             | 1280x1024 | 17.1 | 2013 | [37F3F9CC9655](<Digital/AOC/AOC1719/37F3F9CC9655>) |
| AOC              | AOC1719 | 1719             | 1280x1024 | 17.1 | 2010 | [9A036542ADFF](<Digital/AOC/AOC1719/9A036542ADFF>) |
| AOC              | AOC1759 | E1759Fwu         | 1600x900  | 17.1 | 2014 | [BE43F00380C8](<Digital/AOC/AOC1759/BE43F00380C8>) |
| AOC              | AOC1780 | TFT1780          | 1280x1024 | 17.1 | 2008 | [1EF8DAFB022B](<Digital/AOC/AOC1780/1EF8DAFB022B>) |
| AOC              | AOC1780 | TFT1780          | 1280x1024 | 17.1 | 2007 | [174295170EEA](<Digital/AOC/AOC1780/174295170EEA>) |
| AOC              | AOC1831 | 831W             | 1366x768  | 18.5 | 2010 | [2F53C874AAC3](<Digital/AOC/AOC1831/2F53C874AAC3>) |
| AOC              | AOC1831 | 831W             | 1366x768  | 18.5 |      | [A2FEF7F64351](<Digital/AOC/AOC1831/A2FEF7F64351>) |
| AOC              | AOC1900 | F19              | 1366x768  | 18.5 | 2010 | [74F62969673E](<Digital/AOC/AOC1900/74F62969673E>) |
| AOC              | AOC1900 | F19              | 1366x768  | 18.5 | 2009 | [18545BF9F760](<Digital/AOC/AOC1900/18545BF9F760>) |
| AOC              | AOC1900 | F19              | 1366x768  | 18.5 | 2008 | [505A52DE7374](<Digital/AOC/AOC1900/505A52DE7374>) |
| AOC              | AOC1900 | F19              | 1920x1080 | 18.5 |      | [7514A7FE7129](<Digital/AOC/AOC1900/7514A7FE7129>) |
| AOC              | AOC1901 | 9P1W             | 1366x768  | 18.5 | 2019 | [C2E71F2364C0](<Digital/AOC/AOC1901/C2E71F2364C0>) |
| AOC              | AOC1902 | 912Sws-1         | 1440x900  | 19.1 | 2007 | [A5B466E5FD87](<Digital/AOC/AOC1902/A5B466E5FD87>) |
| AOC              | AOC1902 | G19LWk           | 1440x900  | 19.1 | 2006 | [5A8E033DAD77](<Digital/AOC/AOC1902/5A8E033DAD77>) |
| AOC              | AOC1907 | LE19W037         | 1360x768  | 18.5 | 2010 | [A14B7788BC59](<Digital/AOC/AOC1907/A14B7788BC59>) |
| AOC              | AOC1907 | 907              | 1280x1024 | 19.1 | 2007 | [B7524E907425](<Digital/AOC/AOC1907/B7524E907425>) |
| AOC              | AOC190A | N19W             | 1440x900  | 19.1 | 2008 | [4D1CC01DAE2D](<Digital/AOC/AOC190A/4D1CC01DAE2D>) |
| AOC              | AOC1912 | 912Vwa           | 1440x900  | 18.6 | 2008 | [278C4B658C7C](<Digital/AOC/AOC1912/278C4B658C7C>) |
| AOC              | AOC1912 | 912Vwa           | 1440x900  | 18.6 | 2007 | [4EC014848040](<Digital/AOC/AOC1912/4EC014848040>) |
| AOC              | AOC1912 | 912Vwa           | 1440x900  | 18.6 |      | [EC3C9662B077](<Digital/AOC/AOC1912/EC3C9662B077>) |
| AOC              | AOC1913 | 913W             | 1440x900  | 19.1 | 2009 | [C1FC791A9955](<Digital/AOC/AOC1913/C1FC791A9955>) |
| AOC              | AOC1913 | 913W             | 1440x900  | 19.1 | 2008 | [371AB5EDC610](<Digital/AOC/AOC1913/371AB5EDC610>) |
| AOC              | AOC1916 | 916W             | 1440x900  | 18.6 | 2008 | [64E5FC7390DA](<Digital/AOC/AOC1916/64E5FC7390DA>) |
| AOC              | AOC1916 | 916W             | 1440x900  | 19.1 | 2008 | [EF1EB6D85F7E](<Digital/AOC/AOC1916/EF1EB6D85F7E>) |
| AOC              | AOC1916 | 916W             | 1440x900  | 18.6 | 2007 | [C9F56755DF0F](<Digital/AOC/AOC1916/C9F56755DF0F>) |
| AOC              | AOC1917 | 917W             | 1440x900  | 18.6 | 2008 | [018EE2F3A5A8](<Digital/AOC/AOC1917/018EE2F3A5A8>) |
| AOC              | AOC1919 | 919              | 1280x1024 | 19.1 | 2012 | [A512AEE5BC94](<Digital/AOC/AOC1919/A512AEE5BC94>) |
| AOC              | AOC1919 | 919W             | 1440x900  | 18.6 | 2011 | [089F12A7EE0A](<Digital/AOC/AOC1919/089F12A7EE0A>) |
| AOC              | AOC1919 | 919              | 1280x1024 | 19.1 | 2010 | [7B583ABBE304](<Digital/AOC/AOC1919/7B583ABBE304>) |
| AOC              | AOC1919 | 919W             | 1440x900  | 18.6 | 2010 | [A1615568589D](<Digital/AOC/AOC1919/A1615568589D>) |
| AOC              | AOC1919 | 919              | 1280x1024 | 19.1 | 2008 | [0F4A7FE1A0CE](<Digital/AOC/AOC1919/0F4A7FE1A0CE>) |
| AOC              | AOC1919 | 919Wx            | 1680x1050 | 21.7 | 2008 | [CBDBB9A3A738](<Digital/AOC/AOC1919/CBDBB9A3A738>) |
| AOC              | AOC1919 | 919              | 1280x1024 | 19.1 |      | [440FE78AB30B](<Digital/AOC/AOC1919/440FE78AB30B>) |
| AOC              | AOC191A | L19W981          | 1440x900  | 18.6 | 2009 | [018C1813F926](<Digital/AOC/AOC191A/018C1813F926>) |
| AOC              | AOC1931 | L19W831          | 1280x1024 | 19.1 | 2009 | [86F39E6B3A18](<Digital/AOC/AOC1931/86F39E6B3A18>) |
| AOC              | AOC1931 | 931Wx            | 1680x1050 | 21.7 | 2009 | [ECFC524A5FC5](<Digital/AOC/AOC1931/ECFC524A5FC5>) |
| AOC              | AOC1931 | 931Wx            | 1680x1050 | 21.7 | 2008 | [686F8003DA46](<Digital/AOC/AOC1931/686F8003DA46>) |
| AOC              | AOC1931 | L19W831          | 1280x1024 | 19.1 | 2008 | [A99092CFB363](<Digital/AOC/AOC1931/A99092CFB363>) |
| AOC              | AOC1936 | 936W             | 1366x768  | 18.5 | 2010 | [3B0C2151780F](<Digital/AOC/AOC1936/3B0C2151780F>) |
| AOC              | AOC1936 | 936W             | 1366x768  | 18.5 | 2009 | [12D91C17ED6E](<Digital/AOC/AOC1936/12D91C17ED6E>) |
| AOC              | AOC1936 | 936W             | 1920x1080 | 18.5 |      | [0059652BE0E8](<Digital/AOC/AOC1936/0059652BE0E8>) |
| AOC              | AOC1941 | 1941W            | 1366x768  | 18.5 | 2010 | [74B37E774FCA](<Digital/AOC/AOC1941/74B37E774FCA>) |
| AOC              | AOC1941 | 1941W            | 1366x768  | 18.5 |      | [A35E79800D21](<Digital/AOC/AOC1941/A35E79800D21>) |
| AOC              | AOC1942 | T942we           | 1366x768  | 18.5 | 2010 | [2D82A5A2E062](<Digital/AOC/AOC1942/2D82A5A2E062>) |
| AOC              | AOC1943 | 1943W            | 1366x768  | 18.5 | 2011 | [6DB723018710](<Digital/AOC/AOC1943/6DB723018710>) |
| AOC              | AOC1943 | 1943W            | 1366x768  | 18.5 | 2010 | [1820C11BE14B](<Digital/AOC/AOC1943/1820C11BE14B>) |
| AOC              | AOC1950 | 1950W            | 1366x768  | 18.5 | 2014 | [147E2C70BCD8](<Digital/AOC/AOC1950/147E2C70BCD8>) |
| AOC              | AOC1950 | 1950W            | 1366x768  | 18.5 | 2013 | [3F1D8378AE79](<Digital/AOC/AOC1950/3F1D8378AE79>) |
| AOC              | AOC1950 | 1950W            | 1366x768  | 18.5 | 2012 | [7413E1510719](<Digital/AOC/AOC1950/7413E1510719>) |
| AOC              | AOC1950 | 1950W            | 1366x768  | 18.5 | 2011 | [052FB67C2330](<Digital/AOC/AOC1950/052FB67C2330>) |
| AOC              | AOC1950 | 1950W            | 1366x768  | 18.5 |      | [16EA5B7900A1](<Digital/AOC/AOC1950/16EA5B7900A1>) |
| AOC              | AOC1953 | M19W531          | 1440x900  | 18.6 | 2007 | [34E422EE935C](<Digital/AOC/AOC1953/34E422EE935C>) |
| AOC              | AOC1954 | T954we           | 1360x768  | 18.5 | 2011 | [0623B4786543](<Digital/AOC/AOC1954/0623B4786543>) |
| AOC              | AOC1960 | 1960R            | 1280x1024 | 19.1 | 2018 | [24CADF05051F](<Digital/AOC/AOC1960/24CADF05051F>) |
| AOC              | AOC1960 | 1960R            | 1280x1024 | 19.1 | 2017 | [C3CA8C8AE424](<Digital/AOC/AOC1960/C3CA8C8AE424>) |
| AOC              | AOC1960 | 1960R            | 1280x1024 | 19.1 | 2014 | [F23DE21C3FBD](<Digital/AOC/AOC1960/F23DE21C3FBD>) |
| AOC              | AOC1960 | 1960             | 1440x900  | 19.1 | 2013 | [2B28B2EB4E47](<Digital/AOC/AOC1960/2B28B2EB4E47>) |
| AOC              | AOC1960 | 1960W            | 1366x768  | 18.5 | 2012 | [B5FF0AFDEF05](<Digital/AOC/AOC1960/B5FF0AFDEF05>) |
| AOC              | AOC1966 | 966W             | 1366x768  | 18.5 | 2012 | [0FF6B3D95E0D](<Digital/AOC/AOC1966/0FF6B3D95E0D>) |
| AOC              | AOC1970 | 1970W-1          | 1366x768  | 18.5 | 2024 | [13E5B985F538](<Digital/AOC/AOC1970/13E5B985F538>) |
| AOC              | AOC1970 | 1970W-1          | 1366x768  | 18.5 | 2022 | [1B043935B338](<Digital/AOC/AOC1970/1B043935B338>) |
| AOC              | AOC1970 | 1970W-1          | 1366x768  | 18.5 | 2021 | [342A8ED1DCBE](<Digital/AOC/AOC1970/342A8ED1DCBE>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2020 | [06D4EA793D17](<Digital/AOC/AOC1970/06D4EA793D17>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2019 | [20449350006C](<Digital/AOC/AOC1970/20449350006C>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2018 | [20B5B15B7F0B](<Digital/AOC/AOC1970/20B5B15B7F0B>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2017 | [0E194B99EDEA](<Digital/AOC/AOC1970/0E194B99EDEA>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2016 | [2BFD13B8C83A](<Digital/AOC/AOC1970/2BFD13B8C83A>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2015 | [54428F1C4CCD](<Digital/AOC/AOC1970/54428F1C4CCD>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2014 | [24EE8F660042](<Digital/AOC/AOC1970/24EE8F660042>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 | 2013 | [B44E4447EFAC](<Digital/AOC/AOC1970/B44E4447EFAC>) |
| AOC              | AOC1970 | 1970W            | 1366x768  | 18.5 |      | [0BC61684268E](<Digital/AOC/AOC1970/0BC61684268E>) |
| AOC              | AOC1970 | 1970W            | 1920x1080 | 18.5 |      | [3710A1B9CCF1](<Digital/AOC/AOC1970/3710A1B9CCF1>) |
| AOC              | AOC1975 | 1975W            | 1366x768  | 18.5 | 2017 | [C846F01E2DF0](<Digital/AOC/AOC1975/C846F01E2DF0>) |
| AOC              | AOC1980 | 912Sw            | 1440x900  | 18.6 | 2008 | [A8DF48E8D70C](<Digital/AOC/AOC1980/A8DF48E8D70C>) |
| AOC              | AOC1980 | TFT1980          | 1280x1024 | 19.1 | 2007 | [F78E1EA35C12](<Digital/AOC/AOC1980/F78E1EA35C12>) |
| AOC              | AOC1980 | TFT1980          | 1280x1024 | 19.1 | 2006 | [FDBB3B327BE7](<Digital/AOC/AOC1980/FDBB3B327BE7>) |
| AOC              | AOC1982 | LW98             | 1440x900  | 18.6 | 2007 | [1E289DA8677D](<Digital/AOC/AOC1982/1E289DA8677D>) |
| AOC              | AOC1993 | L19W931          | 1360x768  | 19.1 | 2009 | [8F428DC9721D](<Digital/AOC/AOC1993/8F428DC9721D>) |
| AOC              | AOC19A9 | L19WA91          | 1360x768  | 26.1 | 2009 | [C7361069E8C4](<Digital/AOC/AOC19A9/C7361069E8C4>) |
| AOC              | AOC19B8 | L19WB81          | 1360x768  | 19.5 | 2009 | [CB5E246CFD59](<Digital/AOC/AOC19B8/CB5E246CFD59>) |
| AOC              | AOC2001 | 20E1W            | 1600x900  | 19.4 | 2022 | [7F3588AF02A7](<Digital/AOC/AOC2001/7F3588AF02A7>) |
| AOC              | AOC2001 | 20E1W            | 1600x900  | 19.4 | 2021 | [444CCCAC8D8C](<Digital/AOC/AOC2001/444CCCAC8D8C>) |
| AOC              | AOC2001 | 20E1W            | 1600x900  | 19.4 | 2020 | [3C6FA67A999B](<Digital/AOC/AOC2001/3C6FA67A999B>) |
| AOC              | AOC2001 | 20E1W            | 1600x900  | 19.4 | 2019 | [B36E4326D339](<Digital/AOC/AOC2001/B36E4326D339>) |
| AOC              | AOC2001 | 2019Vwal         | 1680x1050 | 20.0 | 2008 | [249A0D4E4CAD](<Digital/AOC/AOC2001/249A0D4E4CAD>) |
| AOC              | AOC2003 | 203w             | 1680x1050 | 20.0 | 2008 | [4DD5352371A4](<Digital/AOC/AOC2003/4DD5352371A4>) |
| AOC              | AOC2003 | 203w             | 1680x1050 | 20.0 |      | [9E6D44FC6E9E](<Digital/AOC/AOC2003/9E6D44FC6E9E>) |
| AOC              | AOC2023 | 2023W            | 1600x900  | 19.4 | 2014 | [0AE01BF9B385](<Digital/AOC/AOC2023/0AE01BF9B385>) |
| AOC              | AOC2023 | 2023W            | 1600x900  | 19.4 | 2013 | [28D6F270DF0B](<Digital/AOC/AOC2023/28D6F270DF0B>) |
| AOC              | AOC2030 | 203Sw            | 1680x1050 | 20.0 | 2007 | [0097D8CCD775](<Digital/AOC/AOC2030/0097D8CCD775>) |
| AOC              | AOC2036 | 2036             | 1600x900  | 19.9 | 2011 | [7ED0D090DA34](<Digital/AOC/AOC2036/7ED0D090DA34>) |
| AOC              | AOC2036 | 2036             | 1600x900  | 19.9 | 2010 | [2CBA6EB077E5](<Digital/AOC/AOC2036/2CBA6EB077E5>) |
| AOC              | AOC2036 | 2036             | 1600x900  | 19.9 | 2009 | [38670C4EC4FB](<Digital/AOC/AOC2036/38670C4EC4FB>) |
| AOC              | AOC2036 | 2036             | 1920x1080 | 19.9 |      | [632DA62959B1](<Digital/AOC/AOC2036/632DA62959B1>) |
| AOC              | AOC2040 | 2040             | 1600x900  | 19.9 | 2010 | [35DD61BB1905](<Digital/AOC/AOC2040/35DD61BB1905>) |
| AOC              | AOC2041 | 2041             | 1600x900  | 19.9 | 2010 | [8B848D4C1B7B](<Digital/AOC/AOC2041/8B848D4C1B7B>) |
| AOC              | AOC2043 | 2043             | 1600x900  | 19.9 | 2012 | [2D394171D93A](<Digital/AOC/AOC2043/2D394171D93A>) |
| AOC              | AOC2043 | 2043             | 1600x900  | 19.9 | 2011 | [6A034903D05D](<Digital/AOC/AOC2043/6A034903D05D>) |
| AOC              | AOC2043 | 2043             | 1600x900  | 19.9 | 2010 | [2FFDBA6C473B](<Digital/AOC/AOC2043/2FFDBA6C473B>) |
| AOC              | AOC2043 | 2043             | 1600x900  | 19.9 |      | [23F85529223B](<Digital/AOC/AOC2043/23F85529223B>) |
| AOC              | AOC2050 | 2050W            | 1600x900  | 19.4 | 2015 | [83AD8F2166C5](<Digital/AOC/AOC2050/83AD8F2166C5>) |
| AOC              | AOC2050 | 2050W            | 1600x900  | 19.4 | 2014 | [07A4269F4A8D](<Digital/AOC/AOC2050/07A4269F4A8D>) |
| AOC              | AOC2050 | 2050             | 1600x900  | 19.9 | 2013 | [0AA8290638A1](<Digital/AOC/AOC2050/0AA8290638A1>) |
| AOC              | AOC2050 | 2050W            | 1600x900  | 19.4 | 2013 | [3DABADACD798](<Digital/AOC/AOC2050/3DABADACD798>) |
| AOC              | AOC2050 | 2050             | 1600x900  | 19.9 | 2012 | [3C9AD04E6DBF](<Digital/AOC/AOC2050/3C9AD04E6DBF>) |
| AOC              | AOC2050 | 2050             | 1600x900  | 19.9 | 2011 | [AC71F5E2B986](<Digital/AOC/AOC2050/AC71F5E2B986>) |
| AOC              | AOC2050 | 2050             | 1600x900  | 19.9 |      | [01C01B7335E9](<Digital/AOC/AOC2050/01C01B7335E9>) |
| AOC              | AOC2051 | 2051             | 1600x900  | 19.9 | 2012 | [99A4DCBD7492](<Digital/AOC/AOC2051/99A4DCBD7492>) |
| AOC              | AOC2060 | 2060W3           | 1920x1080 | 19.7 | 2019 | [26A797DCCE5B](<Digital/AOC/AOC2060/26A797DCCE5B>) |
| AOC              | AOC2060 | 2060W3           | 1920x1080 | 19.7 | 2018 | [3D46471055C2](<Digital/AOC/AOC2060/3D46471055C2>) |
| AOC              | AOC2060 | 2060W3           | 1920x1080 | 19.7 | 2017 | [0E895D14848D](<Digital/AOC/AOC2060/0E895D14848D>) |
| AOC              | AOC2060 | 2060W3           | 1920x1080 | 19.7 | 2016 | [18DF40DE6CF4](<Digital/AOC/AOC2060/18DF40DE6CF4>) |
| AOC              | AOC2060 | 2060W            | 1600x900  | 19.4 | 2015 | [098CB3AF9298](<Digital/AOC/AOC2060/098CB3AF9298>) |
| AOC              | AOC2060 | 2060W3           | 1920x1080 | 19.7 | 2015 | [5767D94AB569](<Digital/AOC/AOC2060/5767D94AB569>) |
| AOC              | AOC2060 | 2060W            | 1600x900  | 19.4 | 2014 | [3628FD81B7C1](<Digital/AOC/AOC2060/3628FD81B7C1>) |
| AOC              | AOC2060 | 2060W            | 1600x900  | 19.4 | 2013 | [00B27F15202C](<Digital/AOC/AOC2060/00B27F15202C>) |
| AOC              | AOC2060 | 2060W            | 1600x900  | 19.4 | 2012 | [381098F4A0C8](<Digital/AOC/AOC2060/381098F4A0C8>) |
| AOC              | AOC2060 | 2060             | 1600x900  | 21.3 | 2012 | [39AFBEAFE6D4](<Digital/AOC/AOC2060/39AFBEAFE6D4>) |
| AOC              | AOC2060 | 2060W3           | 1920x1080 | 19.7 |      | [D3238936363E](<Digital/AOC/AOC2060/D3238936363E>) |
| AOC              | AOC2070 | 2070L            | 1366x768  | 19.4 | 2022 | [19984C716F1F](<Digital/AOC/AOC2070/19984C716F1F>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2022 | [29F5AB1CDCE3](<Digital/AOC/AOC2070/29F5AB1CDCE3>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2021 | [834AE8A9D9ED](<Digital/AOC/AOC2070/834AE8A9D9ED>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2020 | [00F8EAA02467](<Digital/AOC/AOC2070/00F8EAA02467>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2019 | [778404562327](<Digital/AOC/AOC2070/778404562327>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2018 | [002AB1741D68](<Digital/AOC/AOC2070/002AB1741D68>) |
| AOC              | AOC2070 | 2070L            | 1366x768  | 19.4 | 2018 | [6482F98420DE](<Digital/AOC/AOC2070/6482F98420DE>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2017 | [0E0AA031ECDC](<Digital/AOC/AOC2070/0E0AA031ECDC>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2015 | [CE9D5346B6B9](<Digital/AOC/AOC2070/CE9D5346B6B9>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2014 | [2F90FEB43A62](<Digital/AOC/AOC2070/2F90FEB43A62>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 | 2013 | [0C22BA51F701](<Digital/AOC/AOC2070/0C22BA51F701>) |
| AOC              | AOC2070 | 2070W            | 1600x900  | 19.4 |      | [2D78649B9021](<Digital/AOC/AOC2070/2D78649B9021>) |
| AOC              | AOC2072 | 2072W            | 1600x900  | 20.4 | 2015 | [4B1BC367D11C](<Digital/AOC/AOC2072/4B1BC367D11C>) |
| AOC              | AOC2080 | 2080W            | 1440x900  | 19.4 | 2017 | [36BF3B2718CB](<Digital/AOC/AOC2080/36BF3B2718CB>) |
| AOC              | AOC2080 | 2080W            | 1440x900  | 19.4 | 2016 | [315138C2ADF6](<Digital/AOC/AOC2080/315138C2ADF6>) |
| AOC              | AOC2116 | 2116S            | 1680x1050 | 21.4 | 2007 | [6F4D36C3D9A3](<Digital/AOC/AOC2116/6F4D36C3D9A3>) |
| AOC              | AOC2200 | 2200W            | 1920x1080 | 21.7 | 2019 | [884C7CE0CAA3](<Digital/AOC/AOC2200/884C7CE0CAA3>) |
| AOC              | AOC2200 | 2200W            | 1920x1080 | 21.7 | 2018 | [21C1A349CD43](<Digital/AOC/AOC2200/21C1A349CD43>) |
| AOC              | AOC2200 | 2200W            | 1920x1080 | 21.7 | 2017 | [10A52EAB009C](<Digital/AOC/AOC2200/10A52EAB009C>) |
| AOC              | AOC2200 | F22              | 1920x1080 | 21.1 | 2011 | [07E52635D5E2](<Digital/AOC/AOC2200/07E52635D5E2>) |
| AOC              | AOC2200 | F22              | 1920x1080 | 21.1 | 2010 | [41392E8058D2](<Digital/AOC/AOC2200/41392E8058D2>) |
| AOC              | AOC2200 | V22              | 1680x1050 | 24.0 | 2010 | [9C94394E408D](<Digital/AOC/AOC2200/9C94394E408D>) |
| AOC              | AOC2200 | F22              | 1920x1080 | 21.1 | 2009 | [1B457F5C97F8](<Digital/AOC/AOC2200/1B457F5C97F8>) |
| AOC              | AOC2200 | e22t             | 1920x1080 | 21.7 | 2009 | [516704718222](<Digital/AOC/AOC2200/516704718222>) |
| AOC              | AOC2200 | V22              | 1680x1050 | 24.0 | 2009 | [5A3E4E2CB262](<Digital/AOC/AOC2200/5A3E4E2CB262>) |
| AOC              | AOC2200 | V22              | 1920x1080 | 24.0 |      | [E2060A0AAD5A](<Digital/AOC/AOC2200/E2060A0AAD5A>) |
| AOC              | AOC2201 | 22B15HN          | 1920x1080 | 21.5 | 2025 | [1EF3FC8D9C2C](<Digital/AOC/AOC2201/1EF3FC8D9C2C>) |
| AOC              | AOC2201 | 22B1WG5          | 1920x1080 | 21.5 | 2023 | [1F5A412B31AE](<Digital/AOC/AOC2201/1F5A412B31AE>) |
| AOC              | AOC2201 | 22B1WG5          | 1920x1080 | 21.5 | 2022 | [23C569215B7A](<Digital/AOC/AOC2201/23C569215B7A>) |
| AOC              | AOC2201 | 22E1W            | 1920x1080 | 21.7 | 2022 | [29BE0A4F59B8](<Digital/AOC/AOC2201/29BE0A4F59B8>) |
| AOC              | AOC2201 | 22B1W            | 1920x1080 | 21.7 | 2021 | [0D586EFC5D6B](<Digital/AOC/AOC2201/0D586EFC5D6B>) |
| AOC              | AOC2201 | 22B1WG5          | 1920x1080 | 21.5 | 2021 | [4CD1417F778D](<Digital/AOC/AOC2201/4CD1417F778D>) |
| AOC              | AOC2201 | 22B1W            | 1920x1080 | 21.7 | 2020 | [1B9F9EA6E89A](<Digital/AOC/AOC2201/1B9F9EA6E89A>) |
| AOC              | AOC2201 | 22B1W            | 1920x1080 | 21.7 | 2019 | [0BE3A2B68DD9](<Digital/AOC/AOC2201/0BE3A2B68DD9>) |
| AOC              | AOC2201 | 22P1W            | 1920x1080 | 21.7 | 2018 | [0997AE4DBF67](<Digital/AOC/AOC2201/0997AE4DBF67>) |
| AOC              | AOC2201 | 22E1W            | 1920x1080 | 21.7 |      | [1A8E7CD5AF4F](<Digital/AOC/AOC2201/1A8E7CD5AF4F>) |
| AOC              | AOC2202 | 22B2HM2B         | 1920x1080 | 21.5 | 2024 | [150BFB1F5052](<Digital/AOC/AOC2202/150BFB1F5052>) |
| AOC              | AOC2202 | 22B2WG5          | 1920x1080 | 21.7 | 2024 | [CA85ACF9D50B](<Digital/AOC/AOC2202/CA85ACF9D50B>) |
| AOC              | AOC2202 | 22B2WG5          | 1920x1080 | 21.7 | 2023 | [2A2D2FCE1BE9](<Digital/AOC/AOC2202/2A2D2FCE1BE9>) |
| AOC              | AOC2202 | 22B2WG5          | 1920x1080 | 21.7 | 2022 | [00F1A0059689](<Digital/AOC/AOC2202/00F1A0059689>) |
| AOC              | AOC2202 | 22B1WG5          | 1920x1080 | 21.5 | 2022 | [C196FA719B8A](<Digital/AOC/AOC2202/C196FA719B8A>) |
| AOC              | AOC2202 | 22B2WG5          | 1920x1080 | 21.7 | 2021 | [35260AB08A3E](<Digital/AOC/AOC2202/35260AB08A3E>) |
| AOC              | AOC2202 | 22V2WG5          | 1920x1080 | 21.7 | 2020 | [00C31ED96A3D](<Digital/AOC/AOC2202/00C31ED96A3D>) |
| AOC              | AOC2202 | 22V2WG5          | 1920x1080 | 21.7 | 2019 | [555F38219C6F](<Digital/AOC/AOC2202/555F38219C6F>) |
| AOC              | AOC2202 | 22V2WG5          | 1920x1080 | 21.7 | 2018 | [3509DA7EBF29](<Digital/AOC/AOC2202/3509DA7EBF29>) |
| AOC              | AOC2203 | 22B30HM2         | 1920x1080 | 21.5 | 2025 | [DF6C8C5EB227](<Digital/AOC/AOC2203/DF6C8C5EB227>) |
| AOC              | AOC2203 | 22B35HM2         | 1920x1080 | 21.5 | 2024 | [007968CE5A3E](<Digital/AOC/AOC2203/007968CE5A3E>) |
| AOC              | AOC2203 | 22B3HM           | 1920x1080 | 21.7 | 2023 | [5D5DC14A068A](<Digital/AOC/AOC2203/5D5DC14A068A>) |
| AOC              | AOC2203 | 22V2WG5          | 1920x1080 | 21.7 | 2020 | [8ACDFD5E7606](<Digital/AOC/AOC2203/8ACDFD5E7606>) |
| AOC              | AOC2207 | LE22H037         | 1920x1080 | 21.7 | 2010 | [60AF14B0F652](<Digital/AOC/AOC2207/60AF14B0F652>) |
| AOC              | AOC2210 | LE22H067         | 1920x1080 | 21.7 | 2010 | [342F6487A061](<Digital/AOC/AOC2210/342F6487A061>) |
| AOC              | AOC2210 | 210V             | 1680x1050 | 22.0 | 2007 | [BADECE3242DE](<Digital/AOC/AOC2210/BADECE3242DE>) |
| AOC              | AOC2212 | 2212             | 1920x1080 | 22.0 |      | [BB099CDC4FCA](<Digital/AOC/AOC2212/BB099CDC4FCA>) |
| AOC              | AOC2215 | LE22H158         | 1920x1080 | 21.7 | 2011 | [84D3243FFEA0](<Digital/AOC/AOC2215/84D3243FFEA0>) |
| AOC              | AOC2216 | 2216             | 1680x1050 | 22.0 | 2008 | [14F6CFB9421B](<Digital/AOC/AOC2216/14F6CFB9421B>) |
| AOC              | AOC2217 | 2217             | 1680x1050 | 22.0 | 2009 | [02C1219675B5](<Digital/AOC/AOC2217/02C1219675B5>) |
| AOC              | AOC2217 | 2217             | 1680x1050 | 22.0 | 2008 | [71A9B4637B3F](<Digital/AOC/AOC2217/71A9B4637B3F>) |
| AOC              | AOC2217 | 2217             | 1680x1050 | 22.0 | 2007 | [C9A4D39A72FB](<Digital/AOC/AOC2217/C9A4D39A72FB>) |
| AOC              | AOC2218 | LE22H138         | 1920x1080 | 21.7 | 2011 | [4E392B8F9916](<Digital/AOC/AOC2218/4E392B8F9916>) |
| AOC              | AOC2218 | 2218             | 1680x1050 | 24.0 | 2008 | [7427FF3AA953](<Digital/AOC/AOC2218/7427FF3AA953>) |
| AOC              | AOC2219 | E2219            | 1680x1050 | 22.0 | 2012 | [5B0C21476D51](<Digital/AOC/AOC2219/5B0C21476D51>) |
| AOC              | AOC2219 | 2219             | 1680x1050 | 22.0 | 2011 | [4DA9C747E834](<Digital/AOC/AOC2219/4DA9C747E834>) |
| AOC              | AOC2219 | 2219             | 1680x1050 | 22.0 | 2010 | [ED0DD39A1941](<Digital/AOC/AOC2219/ED0DD39A1941>) |
| AOC              | AOC2219 | 2219             | 1680x1050 | 22.0 | 2009 | [4DE7D7CAFD51](<Digital/AOC/AOC2219/4DE7D7CAFD51>) |
| AOC              | AOC2220 | 2220W            | 1920x1080 | 21.7 | 2015 | [51D7AC7621CB](<Digital/AOC/AOC2220/51D7AC7621CB>) |
| AOC              | AOC2220 | 2220W            | 1920x1080 | 21.7 | 2014 | [B509314CC2A7](<Digital/AOC/AOC2220/B509314CC2A7>) |
| AOC              | AOC2223 | 2223W            | 1920x1080 | 21.7 | 2015 | [43B36CEBA88A](<Digital/AOC/AOC2223/43B36CEBA88A>) |
| AOC              | AOC2223 | 2223W            | 1920x1080 | 21.7 | 2013 | [1D060C384CBA](<Digital/AOC/AOC2223/1D060C384CBA>) |
| AOC              | AOC2228 | 2228W            | 1920x1080 | 21.7 | 2016 | [51AA3354B8E2](<Digital/AOC/AOC2228/51AA3354B8E2>) |
| AOC              | AOC2230 | 2230             | 1680x1050 | 24.0 | 2009 | [230A47CD59E1](<Digital/AOC/AOC2230/230A47CD59E1>) |
| AOC              | AOC2230 | 2230             | 1680x1050 | 24.0 | 2008 | [225089C81768](<Digital/AOC/AOC2230/225089C81768>) |
| AOC              | AOC2230 | 212Va            | 1680x1050 | 22.0 | 2008 | [2FC7D34F2DA9](<Digital/AOC/AOC2230/2FC7D34F2DA9>) |
| AOC              | AOC2230 | 212Va            | 1680x1050 | 22.0 | 2007 | [EF161AC85C42](<Digital/AOC/AOC2230/EF161AC85C42>) |
| AOC              | AOC2231 | L22W931          | 1360x768  | 26.1 | 2009 | [FF91A8EB6B84](<Digital/AOC/AOC2231/FF91A8EB6B84>) |
| AOC              | AOC2236 | 2236             | 1920x1080 | 21.7 | 2011 | [1AFC7F9FA651](<Digital/AOC/AOC2236/1AFC7F9FA651>) |
| AOC              | AOC2236 | 2236             | 1920x1080 | 21.7 | 2010 | [2C08841539DA](<Digital/AOC/AOC2236/2C08841539DA>) |
| AOC              | AOC2236 | 2236             | 1920x1080 | 21.7 | 2009 | [0CCB5A6FE0E4](<Digital/AOC/AOC2236/0CCB5A6FE0E4>) |
| AOC              | AOC2236 | 2236             | 1920x1080 | 21.7 |      | [3143A92C23DC](<Digital/AOC/AOC2236/3143A92C23DC>) |
| AOC              | AOC2239 | 2239             | 1920x1080 | 21.7 | 2010 | [05A050BC75D2](<Digital/AOC/AOC2239/05A050BC75D2>) |
| AOC              | AOC2240 | 2240w            | 1920x1080 | 21.7 | 2011 | [A6FCB93D323D](<Digital/AOC/AOC2240/A6FCB93D323D>) |
| AOC              | AOC2240 | 2240w            | 1920x1080 | 21.7 | 2010 | [056A8389ACCF](<Digital/AOC/AOC2240/056A8389ACCF>) |
| AOC              | AOC2241 | 2241W            | 1920x1080 | 21.1 | 2010 | [892A0257387F](<Digital/AOC/AOC2241/892A0257387F>) |
| AOC              | AOC2242 | T2242we          | 1920x1080 | 21.7 | 2010 | [281B4E4C08C0](<Digital/AOC/AOC2242/281B4E4C08C0>) |
| AOC              | AOC2243 | 2243W            | 1920x1080 | 21.7 | 2013 | [07E32DADDF83](<Digital/AOC/AOC2243/07E32DADDF83>) |
| AOC              | AOC2243 | 2243W            | 1920x1080 | 21.7 | 2012 | [0565543243E0](<Digital/AOC/AOC2243/0565543243E0>) |
| AOC              | AOC2243 | 2243W            | 1920x1080 | 21.7 | 2011 | [0BE084588831](<Digital/AOC/AOC2243/0BE084588831>) |
| AOC              | AOC2243 | 2243W            | 1920x1080 | 21.7 | 2010 | [1E45B46403DC](<Digital/AOC/AOC2243/1E45B46403DC>) |
| AOC              | AOC2243 | 2243W            | 1920x1080 | 21.7 |      | [50E0A7B81FCB](<Digital/AOC/AOC2243/50E0A7B81FCB>) |
| AOC              | AOC2250 | 2250W            | 1920x1080 | 21.7 | 2015 | [226BEFD60EBB](<Digital/AOC/AOC2250/226BEFD60EBB>) |
| AOC              | AOC2250 | 2250W            | 1920x1080 | 21.7 | 2014 | [0F9F7C69BA52](<Digital/AOC/AOC2250/0F9F7C69BA52>) |
| AOC              | AOC2250 | 2250W            | 1920x1080 | 21.7 | 2013 | [3A573B26B4FF](<Digital/AOC/AOC2250/3A573B26B4FF>) |
| AOC              | AOC2250 | 2250W            | 1920x1080 | 21.7 | 2012 | [02E92EC4619E](<Digital/AOC/AOC2250/02E92EC4619E>) |
| AOC              | AOC2250 | 2250             | 1680x1050 | 22.0 | 2012 | [6D6698ED91F3](<Digital/AOC/AOC2250/6D6698ED91F3>) |
| AOC              | AOC2250 | 2250W            | 1920x1080 | 21.7 | 2011 | [01B49E93238A](<Digital/AOC/AOC2250/01B49E93238A>) |
| AOC              | AOC2251 | 2251WH           | 1920x1080 | 21.7 | 2012 | [114375F08812](<Digital/AOC/AOC2251/114375F08812>) |
| AOC              | AOC2251 | 2251w            | 1920x1080 | 21.7 | 2011 | [EBE75389795B](<Digital/AOC/AOC2251/EBE75389795B>) |
| AOC              | AOC2251 | E2251Fw          | 1920x1080 | 21.7 |      | [A4651E1A4FA6](<Digital/AOC/AOC2251/A4651E1A4FA6>) |
| AOC              | AOC2252 | 2252W            | 1920x1080 | 21.7 | 2018 | [90177C9BD056](<Digital/AOC/AOC2252/90177C9BD056>) |
| AOC              | AOC2252 | 2252W            | 1920x1080 | 21.7 | 2017 | [32BDCBC5C933](<Digital/AOC/AOC2252/32BDCBC5C933>) |
| AOC              | AOC2252 | 2252W            | 1920x1080 | 21.7 | 2016 | [8B158803A65D](<Digital/AOC/AOC2252/8B158803A65D>) |
| AOC              | AOC2252 | 2252W            | 1920x1080 | 21.7 | 2015 | [A25D4679A8BC](<Digital/AOC/AOC2252/A25D4679A8BC>) |
| AOC              | AOC2252 | 2252W            | 1920x1080 | 21.7 | 2013 | [09C8AC3ABD74](<Digital/AOC/AOC2252/09C8AC3ABD74>) |
| AOC              | AOC2252 | 2252W            | 1920x1080 | 21.7 | 2011 | [5AF40FD4D073](<Digital/AOC/AOC2252/5AF40FD4D073>) |
| AOC              | AOC2255 | T2255we          | 1920x1080 | 21.7 | 2011 | [AD5F3185742C](<Digital/AOC/AOC2255/AD5F3185742C>) |
| AOC              | AOC2258 | 2258W            | 1920x1080 | 21.7 | 2013 | [3A1521CAC791](<Digital/AOC/AOC2258/3A1521CAC791>) |
| AOC              | AOC2260 | 2260WG5          | 1920x1080 | 21.7 | 2020 | [2BC1920D84E5](<Digital/AOC/AOC2260/2BC1920D84E5>) |
| AOC              | AOC2260 | 2260WG5          | 1920x1080 | 21.7 | 2019 | [0ADBF2C62C5F](<Digital/AOC/AOC2260/0ADBF2C62C5F>) |
| AOC              | AOC2260 | 2260WG5          | 1920x1080 | 21.7 | 2018 | [09D1D606C0AE](<Digital/AOC/AOC2260/09D1D606C0AE>) |
| AOC              | AOC2260 | 2260WG5          | 1920x1080 | 21.7 | 2017 | [1A8E1D1C9035](<Digital/AOC/AOC2260/1A8E1D1C9035>) |
| AOC              | AOC2260 | 2260WG5          | 1920x1080 | 21.7 | 2016 | [0426229C7335](<Digital/AOC/AOC2260/0426229C7335>) |
| AOC              | AOC2260 | 2260             | 1680x1050 | 22.0 | 2016 | [7946C4FA4AFB](<Digital/AOC/AOC2260/7946C4FA4AFB>) |
| AOC              | AOC2260 | 2260W            | 1920x1080 | 21.7 | 2015 | [08CD88096C18](<Digital/AOC/AOC2260/08CD88096C18>) |
| AOC              | AOC2260 | 2260W            | 1920x1080 | 21.7 | 2014 | [811074CA2493](<Digital/AOC/AOC2260/811074CA2493>) |
| AOC              | AOC2260 | 2260             | 1680x1050 | 22.0 | 2014 | [87ED6D44C25A](<Digital/AOC/AOC2260/87ED6D44C25A>) |
| AOC              | AOC2260 | 2260W            | 1920x1080 | 21.7 | 2013 | [3979006E270A](<Digital/AOC/AOC2260/3979006E270A>) |
| AOC              | AOC2260 | 2260             | 1680x1050 | 22.0 | 2013 | [8B9C0FF81F8F](<Digital/AOC/AOC2260/8B9C0FF81F8F>) |
| AOC              | AOC2260 | 2260W            | 1920x1080 | 21.7 | 2012 | [03DD0197984D](<Digital/AOC/AOC2260/03DD0197984D>) |
| AOC              | AOC2260 | 2260             | 1680x1050 | 22.0 | 2012 | [88688FFEFE88](<Digital/AOC/AOC2260/88688FFEFE88>) |
| AOC              | AOC2260 | 2260W            | 1920x1080 | 21.7 |      | [0DA8E7EB3CDA](<Digital/AOC/AOC2260/0DA8E7EB3CDA>) |
| AOC              | AOC2261 | 2261W            | 1920x1080 | 21.7 | 2014 | [EDFEB725DE3E](<Digital/AOC/AOC2261/EDFEB725DE3E>) |
| AOC              | AOC2261 | 2261W            | 1920x1080 | 21.7 | 2013 | [63D7B6119768](<Digital/AOC/AOC2261/63D7B6119768>) |
| AOC              | AOC2262 | 2262w            | 1920x1080 | 21.7 | 2015 | [25BD803E3B13](<Digital/AOC/AOC2262/25BD803E3B13>) |
| AOC              | AOC2262 | 2262w            | 1920x1080 | 21.7 | 2013 | [19CA2F300582](<Digital/AOC/AOC2262/19CA2F300582>) |
| AOC              | AOC2262 | 2262w            | 1920x1080 | 21.7 | 2012 | [F407A0429FC5](<Digital/AOC/AOC2262/F407A0429FC5>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2018 | [5240B1383DD1](<Digital/AOC/AOC2267/5240B1383DD1>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2017 | [0919A15B97C4](<Digital/AOC/AOC2267/0919A15B97C4>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2016 | [2A43F56C5322](<Digital/AOC/AOC2267/2A43F56C5322>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2015 | [030D2FD34D49](<Digital/AOC/AOC2267/030D2FD34D49>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2014 | [0F98B04975BB](<Digital/AOC/AOC2267/0F98B04975BB>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2013 | [4B71F8E02B33](<Digital/AOC/AOC2267/4B71F8E02B33>) |
| AOC              | AOC2267 | 2267W            | 1920x1080 | 21.7 | 2012 | [31C8CA6E744A](<Digital/AOC/AOC2267/31C8CA6E744A>) |
| AOC              | AOC2269 | 2269W            | 1920x1080 | 21.7 | 2018 | [64BFA35C6C30](<Digital/AOC/AOC2269/64BFA35C6C30>) |
| AOC              | AOC2269 | 2269WM           | 1920x1080 | 21.7 | 2017 | [0FA518CC033B](<Digital/AOC/AOC2269/0FA518CC033B>) |
| AOC              | AOC2269 | 2269W            | 1920x1080 | 21.7 | 2016 | [019ADAEE1394](<Digital/AOC/AOC2269/019ADAEE1394>) |
| AOC              | AOC2269 | 2269WM           | 1920x1080 | 21.7 | 2015 | [2FC39C284747](<Digital/AOC/AOC2269/2FC39C284747>) |
| AOC              | AOC2269 | 2269WM           | 1920x1080 | 21.7 | 2014 | [1727E67E0F4A](<Digital/AOC/AOC2269/1727E67E0F4A>) |
| AOC              | AOC2269 | 2269W            | 1920x1080 | 21.7 | 2013 | [00FF2AEF65E7](<Digital/AOC/AOC2269/00FF2AEF65E7>) |
| AOC              | AOC2269 | 2269WM           | 1920x1080 | 21.7 |      | [26216C3C3A24](<Digital/AOC/AOC2269/26216C3C3A24>) |
| AOC              | AOC226B | 2269WM           | 1920x1080 | 21.7 | 2016 | [481A87574259](<Digital/AOC/AOC226B/481A87574259>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2023 | [25B892CA95EA](<Digital/AOC/AOC2270/25B892CA95EA>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2022 | [065211EBC22E](<Digital/AOC/AOC2270/065211EBC22E>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2021 | [07F4E9899F07](<Digital/AOC/AOC2270/07F4E9899F07>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2020 | [0235133153AA](<Digital/AOC/AOC2270/0235133153AA>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2019 | [04E52ED86313](<Digital/AOC/AOC2270/04E52ED86313>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2018 | [10E396A5FF68](<Digital/AOC/AOC2270/10E396A5FF68>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2017 | [05B7092CC208](<Digital/AOC/AOC2270/05B7092CC208>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2016 | [08A5FACB1204](<Digital/AOC/AOC2270/08A5FACB1204>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2015 | [000FDC582001](<Digital/AOC/AOC2270/000FDC582001>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2014 | [1AD4CB64EA67](<Digital/AOC/AOC2270/1AD4CB64EA67>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 | 2013 | [8CB4041BF06F](<Digital/AOC/AOC2270/8CB4041BF06F>) |
| AOC              | AOC2270 | 2270W            | 1920x1080 | 21.7 |      | [872A1BF8CD0F](<Digital/AOC/AOC2270/872A1BF8CD0F>) |
| AOC              | AOC2271 | 2270W            | 1920x1080 | 21.7 | 2018 | [A24978969DB1](<Digital/AOC/AOC2271/A24978969DB1>) |
| AOC              | AOC2272 | 2272W            | 1920x1080 | 21.7 | 2013 | [0FA802DBE62B](<Digital/AOC/AOC2272/0FA802DBE62B>) |
| AOC              | AOC2275 | 2275W            | 1920x1080 | 21.7 | 2019 | [4064FA5E8316](<Digital/AOC/AOC2275/4064FA5E8316>) |
| AOC              | AOC2275 | 2275W            | 1920x1080 | 21.7 | 2018 | [24B6DF73DFB2](<Digital/AOC/AOC2275/24B6DF73DFB2>) |
| AOC              | AOC2275 | 2275W            | 1920x1080 | 21.7 | 2017 | [05F3618D56AD](<Digital/AOC/AOC2275/05F3618D56AD>) |
| AOC              | AOC2275 | 2275W            | 1920x1080 | 21.7 | 2016 | [28FF68495A78](<Digital/AOC/AOC2275/28FF68495A78>) |
| AOC              | AOC2275 | 2275W            | 1920x1080 | 21.7 |      | [204E834B8267](<Digital/AOC/AOC2275/204E834B8267>) |
| AOC              | AOC2276 | 2276WM           | 1920x1080 | 21.7 | 2017 | [226F946FE3A3](<Digital/AOC/AOC2276/226F946FE3A3>) |
| AOC              | AOC2276 | 2276W            | 1920x1080 | 21.7 | 2016 | [1820AA5FD320](<Digital/AOC/AOC2276/1820AA5FD320>) |
| AOC              | AOC2276 | 2276WM           | 1920x1080 | 21.7 | 2015 | [50A92D2C899E](<Digital/AOC/AOC2276/50A92D2C899E>) |
| AOC              | AOC2276 | 2276W            | 1920x1080 | 21.7 | 2014 | [21BF2981EFB5](<Digital/AOC/AOC2276/21BF2981EFB5>) |
| AOC              | AOC2279 | 2279WH           | 1920x1080 | 21.7 | 2018 | [2A94A067BC70](<Digital/AOC/AOC2279/2A94A067BC70>) |
| AOC              | AOC2279 | 2279WH           | 1920x1080 | 21.7 | 2017 | [1FE55DA6C52D](<Digital/AOC/AOC2279/1FE55DA6C52D>) |
| AOC              | AOC2279 | 2279W            | 1920x1080 | 21.7 | 2016 | [BC8A5231BD58](<Digital/AOC/AOC2279/BC8A5231BD58>) |
| AOC              | AOC2279 | 2279WH           | 1920x1080 | 21.7 | 2015 | [0D9A343EBD42](<Digital/AOC/AOC2279/0D9A343EBD42>) |
| AOC              | AOC2279 | 2279WH           | 1920x1080 | 21.7 |      | [02BC79849D16](<Digital/AOC/AOC2279/02BC79849D16>) |
| AOC              | AOC2280 | 2280W            | 1920x1080 | 21.7 | 2018 | [1E20D89A5FE8](<Digital/AOC/AOC2280/1E20D89A5FE8>) |
| AOC              | AOC2280 | 2280W            | 1920x1080 | 21.7 | 2017 | [0AB973D498D4](<Digital/AOC/AOC2280/0AB973D498D4>) |
| AOC              | AOC2280 | 2280W            | 1920x1080 | 21.7 | 2016 | [DC1EA487F50E](<Digital/AOC/AOC2280/DC1EA487F50E>) |
| AOC              | AOC2281 | 2281W            | 1920x1080 | 21.7 | 2019 | [E8715FF99FA8](<Digital/AOC/AOC2281/E8715FF99FA8>) |
| AOC              | AOC2281 | 2281W            | 1920x1080 | 21.7 | 2018 | [09484889FD4B](<Digital/AOC/AOC2281/09484889FD4B>) |
| AOC              | AOC2281 | 2281W            | 1920x1080 | 21.7 | 2017 | [25B568034E49](<Digital/AOC/AOC2281/25B568034E49>) |
| AOC              | AOC2281 | 2281W            | 1920x1080 | 21.7 | 2016 | [37A8540D3450](<Digital/AOC/AOC2281/37A8540D3450>) |
| AOC              | AOC2298 | L22W981          | 1680x1050 | 21.7 | 2008 | [25B9989E6CC4](<Digital/AOC/AOC2298/25B9989E6CC4>) |
| AOC              | AOC2301 | 23E1WX           | 1920x1200 | 22.6 | 2019 | [9C3B9830A32D](<Digital/AOC/AOC2301/9C3B9830A32D>) |
| AOC              | AOC2301 | 23E1WX           | 1920x1200 | 22.6 | 2018 | [8CAD8F985EEE](<Digital/AOC/AOC2301/8CAD8F985EEE>) |
| AOC              | AOC2307 | LE23H037         | 1920x1080 | 23.1 | 2010 | [9E4DC8336BF8](<Digital/AOC/AOC2307/9E4DC8336BF8>) |
| AOC              | AOC2330 | 2330V            | 1920x1080 | 21.1 | 2010 | [07962BAA3515](<Digital/AOC/AOC2330/07962BAA3515>) |
| AOC              | AOC2330 | 2330V            | 1920x1080 | 21.1 | 2009 | [2B886F0F1FE5](<Digital/AOC/AOC2330/2B886F0F1FE5>) |
| AOC              | AOC2341 | 2341             | 1920x1080 | 21.7 | 2010 | [29E90DDC7EE3](<Digital/AOC/AOC2341/29E90DDC7EE3>) |
| AOC              | AOC2343 | 2343             | 1920x1080 | 23.1 | 2013 | [3EC36126F651](<Digital/AOC/AOC2343/3EC36126F651>) |
| AOC              | AOC2343 | 2343             | 1920x1080 | 23.1 | 2012 | [15F9CC6C4397](<Digital/AOC/AOC2343/15F9CC6C4397>) |
| AOC              | AOC2343 | 2343             | 1920x1080 | 23.1 | 2011 | [39EA09DDB733](<Digital/AOC/AOC2343/39EA09DDB733>) |
| AOC              | AOC2343 | 2343             | 1920x1080 | 23.1 | 2010 | [0FB4E9A6DECA](<Digital/AOC/AOC2343/0FB4E9A6DECA>) |
| AOC              | AOC2343 | 2343             | 1920x1080 | 23.1 |      | [F9CA0B9CD4D4](<Digital/AOC/AOC2343/F9CA0B9CD4D4>) |
| AOC              | AOC2350 | 2350             | 1920x1080 | 23.1 | 2013 | [3D2406789AF8](<Digital/AOC/AOC2350/3D2406789AF8>) |
| AOC              | AOC2350 | 2350             | 1920x1080 | 23.1 | 2012 | [3898290E56E0](<Digital/AOC/AOC2350/3898290E56E0>) |
| AOC              | AOC2350 | 2350             | 1920x1080 | 23.1 | 2011 | [1B042931520F](<Digital/AOC/AOC2350/1B042931520F>) |
| AOC              | AOC2351 | 2351             | 1920x1080 | 23.1 | 2013 | [083991D0A021](<Digital/AOC/AOC2351/083991D0A021>) |
| AOC              | AOC2351 | 2351             | 1920x1080 | 23.1 | 2012 | [2C65F8146BF1](<Digital/AOC/AOC2351/2C65F8146BF1>) |
| AOC              | AOC2351 | 2351             | 1920x1080 | 23.1 | 2011 | [56AB2224C81B](<Digital/AOC/AOC2351/56AB2224C81B>) |
| AOC              | AOC2352 | i2352Vh          | 1920x1080 | 23.1 | 2012 | [20CF9B64EFBF](<Digital/AOC/AOC2352/20CF9B64EFBF>) |
| AOC              | AOC2352 | 2352             | 1920x1080 | 23.1 | 2011 | [1C4014D136FC](<Digital/AOC/AOC2352/1C4014D136FC>) |
| AOC              | AOC2352 | 2352             | 1920x1080 | 23.1 |      | [86CB96F8D168](<Digital/AOC/AOC2352/86CB96F8D168>) |
| AOC              | AOC2353 | 2353             | 1920x1080 | 23.1 | 2012 | [6F58B8A45FDA](<Digital/AOC/AOC2353/6F58B8A45FDA>) |
| AOC              | AOC2353 | 2353             | 1920x1080 | 23.1 | 2011 | [08CF0450FF56](<Digital/AOC/AOC2353/08CF0450FF56>) |
| AOC              | AOC2357 | 2357M            | 1920x1080 | 23.1 | 2012 | [3A4B1D1F8F6B](<Digital/AOC/AOC2357/3A4B1D1F8F6B>) |
| AOC              | AOC2360 | 2360             | 1920x1080 | 23.1 | 2014 | [67D26A3F9908](<Digital/AOC/AOC2360/67D26A3F9908>) |
| AOC              | AOC2360 | 2360             | 1920x1080 | 23.1 | 2013 | [03ED08285F38](<Digital/AOC/AOC2360/03ED08285F38>) |
| AOC              | AOC2367 | 2367             | 1920x1080 | 23.1 | 2017 | [8CB54F7FEA21](<Digital/AOC/AOC2367/8CB54F7FEA21>) |
| AOC              | AOC2367 | 2367             | 1920x1080 | 23.1 | 2016 | [063EDB260BAC](<Digital/AOC/AOC2367/063EDB260BAC>) |
| AOC              | AOC2367 | 2367             | 1920x1080 | 23.1 | 2015 | [633CCD487D7C](<Digital/AOC/AOC2367/633CCD487D7C>) |
| AOC              | AOC2367 | 2367             | 1920x1080 | 23.1 | 2014 | [00F996160AE9](<Digital/AOC/AOC2367/00F996160AE9>) |
| AOC              | AOC2367 | 2367             | 1920x1080 | 23.1 | 2013 | [12FF18D7B1C0](<Digital/AOC/AOC2367/12FF18D7B1C0>) |
| AOC              | AOC2367 | 2367             | 1920x1080 | 23.1 | 2012 | [9CDCB8C62CE7](<Digital/AOC/AOC2367/9CDCB8C62CE7>) |
| AOC              | AOC2369 | 2369             | 1920x1080 | 23.1 | 2019 | [0407A6814774](<Digital/AOC/AOC2369/0407A6814774>) |
| AOC              | AOC2369 | 2369M            | 1920x1080 | 23.1 | 2018 | [21FDA3598C9F](<Digital/AOC/AOC2369/21FDA3598C9F>) |
| AOC              | AOC2369 | 2369M            | 1920x1080 | 23.1 | 2017 | [0A4F8DDACF04](<Digital/AOC/AOC2369/0A4F8DDACF04>) |
| AOC              | AOC2369 | 2369M            | 1920x1080 | 23.1 | 2016 | [00AAB98B9419](<Digital/AOC/AOC2369/00AAB98B9419>) |
| AOC              | AOC2369 | 2369             | 1920x1080 | 23.1 | 2015 | [084042D0E17B](<Digital/AOC/AOC2369/084042D0E17B>) |
| AOC              | AOC2369 | 2369M            | 1920x1080 | 23.1 | 2014 | [06DF2533AF33](<Digital/AOC/AOC2369/06DF2533AF33>) |
| AOC              | AOC2369 | 2369M            | 1920x1080 | 23.1 | 2013 | [0355B652A7EC](<Digital/AOC/AOC2369/0355B652A7EC>) |
| AOC              | AOC2369 | 2369M            | 1920x1080 | 23.1 |      | [23833EF8B599](<Digital/AOC/AOC2369/23833EF8B599>) |
| AOC              | AOC2370 | 2370             | 1920x1080 | 23.1 | 2015 | [1ECAE6DD4CC6](<Digital/AOC/AOC2370/1ECAE6DD4CC6>) |
| AOC              | AOC2370 | 2370             | 1920x1080 | 23.1 | 2014 | [5A5341585014](<Digital/AOC/AOC2370/5A5341585014>) |
| AOC              | AOC2370 | 2370             | 1920x1080 | 23.1 | 2013 | [18FF232ADE08](<Digital/AOC/AOC2370/18FF232ADE08>) |
| AOC              | AOC2375 | 2375             | 1920x1080 | 23.1 | 2017 | [7A5976462D4A](<Digital/AOC/AOC2375/7A5976462D4A>) |
| AOC              | AOC2379 | 2379             | 1920x1080 | 23.1 | 2019 | [D10475AA1441](<Digital/AOC/AOC2379/D10475AA1441>) |
| AOC              | AOC2379 | 2379H            | 1920x1080 | 23.1 | 2018 | [F2A1B8554130](<Digital/AOC/AOC2379/F2A1B8554130>) |
| AOC              | AOC2379 | 2379H            | 1920x1080 | 23.1 |      | [53620ED2E10E](<Digital/AOC/AOC2379/53620ED2E10E>) |
| AOC              | AOC2381 | 2381             | 1920x1080 | 23.1 | 2018 | [A80AE194F5DD](<Digital/AOC/AOC2381/A80AE194F5DD>) |
| AOC              | AOC2381 | 2381             | 1920x1080 | 23.1 | 2017 | [60938B32C548](<Digital/AOC/AOC2381/60938B32C548>) |
| AOC              | AOC2381 | 2381             | 1920x1080 | 23.1 | 2016 | [00698F2D0DFB](<Digital/AOC/AOC2381/00698F2D0DFB>) |
| AOC              | AOC2381 | 2381             | 1920x1080 | 23.1 |      | [F6293A0EE524](<Digital/AOC/AOC2381/F6293A0EE524>) |
| AOC              | AOC2400 | 2400W            | 1920x1080 | 24.0 | 2018 | [E3FD06C1EDB8](<Digital/AOC/AOC2400/E3FD06C1EDB8>) |
| AOC              | AOC2400 | V24t             | 1920x1080 | 23.4 | 2015 | [C8A47BE740CF](<Digital/AOC/AOC2400/C8A47BE740CF>) |
| AOC              | AOC2401 | 24E1W1           | 1920x1080 | 24.0 | 2024 | [29D18A596E7F](<Digital/AOC/AOC2401/29D18A596E7F>) |
| AOC              | AOC2401 | 24B1W            | 1920x1080 | 23.4 | 2024 | [31468EA84554](<Digital/AOC/AOC2401/31468EA84554>) |
| AOC              | AOC2401 | 24P1W1           | 1920x1080 | 24.0 | 2023 | [036B53B0EBE3](<Digital/AOC/AOC2401/036B53B0EBE3>) |
| AOC              | AOC2401 | 24B1W            | 1920x1080 | 23.4 | 2023 | [37A5F2356AEF](<Digital/AOC/AOC2401/37A5F2356AEF>) |
| AOC              | AOC2401 | 24B1W            | 1920x1080 | 23.4 | 2022 | [0399F6E11F79](<Digital/AOC/AOC2401/0399F6E11F79>) |
| AOC              | AOC2401 | 24P1W1           | 1920x1080 | 24.0 | 2022 | [0ED708DE28B6](<Digital/AOC/AOC2401/0ED708DE28B6>) |
| AOC              | AOC2401 | 24G1WG3-         | 1920x1080 | 23.4 | 2021 | [0111AFAD5E58](<Digital/AOC/AOC2401/0111AFAD5E58>) |
| AOC              | AOC2401 | 24E1W1           | 1920x1080 | 24.0 | 2021 | [1AC5C5ED564D](<Digital/AOC/AOC2401/1AC5C5ED564D>) |
| AOC              | AOC2401 | 24P1X            | 1920x1200 | 24.0 | 2021 | [2AF9570004C3](<Digital/AOC/AOC2401/2AF9570004C3>) |
| AOC              | AOC2401 | 24E1W1           | 1920x1080 | 24.0 | 2020 | [00D8195B1D10](<Digital/AOC/AOC2401/00D8195B1D10>) |
| AOC              | AOC2401 | 24G1WG4          | 1920x1080 | 23.4 | 2020 | [02C50D163D00](<Digital/AOC/AOC2401/02C50D163D00>) |
| AOC              | AOC2401 | Q24P1W1          | 2560x1440 | 24.0 | 2020 | [1AFCA13D72F3](<Digital/AOC/AOC2401/1AFCA13D72F3>) |
| AOC              | AOC2401 | 24P1X            | 1920x1200 | 24.0 | 2020 | [405206C13826](<Digital/AOC/AOC2401/405206C13826>) |
| AOC              | AOC2401 | 24G1WG4          | 1920x1080 | 23.4 | 2019 | [02000D8DE292](<Digital/AOC/AOC2401/02000D8DE292>) |
| AOC              | AOC2401 | 24P1W1           | 1920x1080 | 24.0 | 2019 | [0210FF316451](<Digital/AOC/AOC2401/0210FF316451>) |
| AOC              | AOC2401 | 24P1X            | 1920x1200 | 24.0 | 2019 | [0F149BD29C4C](<Digital/AOC/AOC2401/0F149BD29C4C>) |
| AOC              | AOC2401 | Q2401W1          | 2560x1440 | 24.0 | 2019 | [405E4A30B5B3](<Digital/AOC/AOC2401/405E4A30B5B3>) |
| AOC              | AOC2401 | 24P1X            | 1920x1200 | 24.0 | 2018 | [035D5DE401C1](<Digital/AOC/AOC2401/035D5DE401C1>) |
| AOC              | AOC2401 | 24B1W            | 1920x1080 | 23.4 | 2018 | [0368D9D89593](<Digital/AOC/AOC2401/0368D9D89593>) |
| AOC              | AOC2401 | 24P1W1           | 1920x1080 | 24.0 | 2018 | [475B77663FA5](<Digital/AOC/AOC2401/475B77663FA5>) |
| AOC              | AOC2401 | 24B1W1           | 1920x1080 | 24.0 |      | [010C5935A5A5](<Digital/AOC/AOC2401/010C5935A5A5>) |
| AOC              | AOC2401 | 24G1WG4          | 1920x1080 | 23.4 |      | [0E66FC9D1C99](<Digital/AOC/AOC2401/0E66FC9D1C99>) |
| AOC              | AOC2402 | 24B2H2           | 1920x1080 | 24.0 | 2025 | [1B18BCAB8054](<Digital/AOC/AOC2402/1B18BCAB8054>) |
| AOC              | AOC2402 | 24G2W1G3-        | 1920x1080 | 24.0 | 2024 | [01DD86A47337](<Digital/AOC/AOC2402/01DD86A47337>) |
| AOC              | AOC2402 | 24G2WG3-         | 1920x1080 | 23.4 | 2024 | [0735D845DE4E](<Digital/AOC/AOC2402/0735D845DE4E>) |
| AOC              | AOC2402 | 24B2HM2          | 1920x1080 | 24.5 | 2024 | [13E8ACE0DB51](<Digital/AOC/AOC2402/13E8ACE0DB51>) |
| AOC              | AOC2402 | 24G2W1G3-        | 1920x1080 | 24.0 | 2023 | [05DD0794F74C](<Digital/AOC/AOC2402/05DD0794F74C>) |
| AOC              | AOC2402 | 24G2WG3-         | 1920x1080 | 23.4 | 2023 | [153AB8AA479E](<Digital/AOC/AOC2402/153AB8AA479E>) |
| AOC              | AOC2402 | 24B2HM2          | 1920x1080 | 24.5 | 2023 | [E38CC4D5546B](<Digital/AOC/AOC2402/E38CC4D5546B>) |
| AOC              | AOC2402 | 24B2W1G5         | 1920x1080 | 24.0 | 2022 | [041B0A743BED](<Digital/AOC/AOC2402/041B0A743BED>) |
| AOC              | AOC2402 | 24G2WG3-         | 1920x1080 | 23.4 | 2022 | [375DED8E54D4](<Digital/AOC/AOC2402/375DED8E54D4>) |
| AOC              | AOC2402 | Q24P2W1G5        | 2560x1440 | 24.0 | 2022 | [3BA77D304D17](<Digital/AOC/AOC2402/3BA77D304D17>) |
| AOC              | AOC2402 | 24G2W1G4         | 1920x1080 | 24.0 | 2021 | [009F7481224D](<Digital/AOC/AOC2402/009F7481224D>) |
| AOC              | AOC2402 | Q24P2W1          | 2560x1440 | 24.0 | 2021 | [1FCE67C174AE](<Digital/AOC/AOC2402/1FCE67C174AE>) |
| AOC              | AOC2402 | 24G2WG3-         | 1920x1080 | 23.4 | 2021 | [2A3DCB479A31](<Digital/AOC/AOC2402/2A3DCB479A31>) |
| AOC              | AOC2402 | 24B2W1           | 1920x1080 | 24.0 | 2020 | [022F22520393](<Digital/AOC/AOC2402/022F22520393>) |
| AOC              | AOC2402 | 24G2WG3-         | 1920x1080 | 23.4 | 2020 | [029E6C5BDB4B](<Digital/AOC/AOC2402/029E6C5BDB4B>) |
| AOC              | AOC2402 | Q24P2W1          | 2560x1440 | 24.0 | 2020 | [76E3204EA184](<Digital/AOC/AOC2402/76E3204EA184>) |
| AOC              | AOC2402 | 24G2W1G4         | 1920x1080 | 24.0 | 2019 | [0588B8862EBE](<Digital/AOC/AOC2402/0588B8862EBE>) |
| AOC              | AOC2402 | 24V2W1G5         | 1920x1080 | 24.0 | 2018 | [0E09584267F0](<Digital/AOC/AOC2402/0E09584267F0>) |
| AOC              | AOC2402 | 24G2W1G4         | 1920x1080 | 24.0 |      | [06CB835CC2AB](<Digital/AOC/AOC2402/06CB835CC2AB>) |
| AOC              | AOC2403 | 24B35HM2         | 1920x1080 | 24.0 | 2025 | [A5E3FD6DEF0E](<Digital/AOC/AOC2403/A5E3FD6DEF0E>) |
| AOC              | AOC2403 | 24B3HA2          | 1920x1080 | 24.0 | 2024 | [02CCE8D8B04E](<Digital/AOC/AOC2403/02CCE8D8B04E>) |
| AOC              | AOC2403 | 24B3HM           | 1920x1080 | 24.0 | 2023 | [21AE1D5197C1](<Digital/AOC/AOC2403/21AE1D5197C1>) |
| AOC              | AOC2403 | 24E3             | 1920x1080 | 24.0 | 2022 | [20E1AA6A8717](<Digital/AOC/AOC2403/20E1AA6A8717>) |
| AOC              | AOC2404 | Q24V4W1G5        | 2560x1440 | 24.0 | 2025 | [F40FF3F5995F](<Digital/AOC/AOC2404/F40FF3F5995F>) |
| AOC              | AOC2404 | Q24V4W1G5        | 2560x1440 | 24.0 | 2024 | [0115CD42C254](<Digital/AOC/AOC2404/0115CD42C254>) |
| AOC              | AOC2404 | Q24V4W1G5        | 2560x1440 | 24.0 | 2023 | [52FC84CC4142](<Digital/AOC/AOC2404/52FC84CC4142>) |
| AOC              | AOC2404 | Q24V4W1G5        | 2560x1440 | 24.0 | 2021 | [10B4BA1C2A27](<Digital/AOC/AOC2404/10B4BA1C2A27>) |
| AOC              | AOC2404 | Q24V4W1G5        | 2560x1440 | 24.0 | 2020 | [774673E5329B](<Digital/AOC/AOC2404/774673E5329B>) |
| AOC              | AOC2407 | LE24H037         | 1920x1080 | 23.4 | 2010 | [A6751917618F](<Digital/AOC/AOC2407/A6751917618F>) |
| AOC              | AOC2407 | LE24H037         | 1920x1080 | 23.4 |      | [E3496300FAAA](<Digital/AOC/AOC2407/E3496300FAAA>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 24.0 | 2019 | [6EB7CD4E4A9E](<Digital/AOC/AOC2410/6EB7CD4E4A9E>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 26.1 | 2019 | [8AFE2661FC5C](<Digital/AOC/AOC2410/8AFE2661FC5C>) |
| AOC              | AOC2410 | AG241QG4         | 1920x1080 | 24.0 | 2019 | [C15D20ACE31A](<Digital/AOC/AOC2410/C15D20ACE31A>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 24.0 | 2018 | [0518661292A3](<Digital/AOC/AOC2410/0518661292A3>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 26.1 | 2018 | [20A865CA004F](<Digital/AOC/AOC2410/20A865CA004F>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 26.1 | 2017 | [0B0871848B93](<Digital/AOC/AOC2410/0B0871848B93>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 24.0 | 2017 | [49043CDC280C](<Digital/AOC/AOC2410/49043CDC280C>) |
| AOC              | AOC2410 | PD241FW1         | 1920x1080 | 24.0 | 2017 | [5EAC480F2C6E](<Digital/AOC/AOC2410/5EAC480F2C6E>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 26.1 | 2016 | [1A17BE12EE14](<Digital/AOC/AOC2410/1A17BE12EE14>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 24.0 | 2016 | [BD518C0E9DE0](<Digital/AOC/AOC2410/BD518C0E9DE0>) |
| AOC              | AOC2410 | LE24H067         | 1920x1080 | 23.4 | 2010 | [334CCFC4BE26](<Digital/AOC/AOC2410/334CCFC4BE26>) |
| AOC              | AOC2410 | AG241QG4         | 2560x1440 | 24.0 |      | [95C30A9BED98](<Digital/AOC/AOC2410/95C30A9BED98>) |
| AOC              | AOC2413 | AG241QG          | 2560x1440 | 24.0 |      | [1B511AC7FC04](<Digital/AOC/AOC2413/1B511AC7FC04>) |
| AOC              | AOC2415 | 24G15N           | 1920x1080 | 24.0 | 2024 | [321F2FA89819](<Digital/AOC/AOC2415/321F2FA89819>) |
| AOC              | AOC2415 | 24G15N           | 1920x1080 | 24.0 | 2023 | [0DC95D397EE1](<Digital/AOC/AOC2415/0DC95D397EE1>) |
| AOC              | AOC2416 | 2416             | 1920x1200 | 24.0 | 2009 | [AEF8C7F2286F](<Digital/AOC/AOC2416/AEF8C7F2286F>) |
| AOC              | AOC2416 | 416              | 1920x1200 | 24.0 | 2008 | [D4B4F08E0481](<Digital/AOC/AOC2416/D4B4F08E0481>) |
| AOC              | AOC2416 | 2416             | 1920x1200 | 24.0 | 2007 | [D76D3A20A78C](<Digital/AOC/AOC2416/D76D3A20A78C>) |
| AOC              | AOC2419 | 419              | 1920x1200 | 25.7 | 2008 | [FF8E73D020BD](<Digital/AOC/AOC2419/FF8E73D020BD>) |
| AOC              | AOC2421 | 2421W            | 1920x1080 | 23.4 | 2014 | [A1B88148BDA9](<Digital/AOC/AOC2421/A1B88148BDA9>) |
| AOC              | AOC2425 | 2425W            | 1920x1080 | 23.4 | 2017 | [2BC2F85682F9](<Digital/AOC/AOC2425/2BC2F85682F9>) |
| AOC              | AOC2425 | 2425W            | 1920x1080 | 23.4 | 2015 | [1DC6C3DFD789](<Digital/AOC/AOC2425/1DC6C3DFD789>) |
| AOC              | AOC2425 | 2425W            | 1920x1080 | 23.4 | 2014 | [21AF9FC2D034](<Digital/AOC/AOC2425/21AF9FC2D034>) |
| AOC              | AOC2425 | 2425W            | 1920x1080 | 23.4 | 2013 | [A2B6636D1BDC](<Digital/AOC/AOC2425/A2B6636D1BDC>) |
| AOC              | AOC2429 | 2429W            | 1920x1080 | 23.4 | 2017 | [8314C7EB656E](<Digital/AOC/AOC2429/8314C7EB656E>) |
| AOC              | AOC2429 | 2429W            | 1920x1080 | 23.4 | 2016 | [24D2556A9454](<Digital/AOC/AOC2429/24D2556A9454>) |
| AOC              | AOC2431 | TV               | 1920x1080 | 23.1 | 2015 | [6CBB883B0E3B](<Digital/AOC/AOC2431/6CBB883B0E3B>) |
| AOC              | AOC2434 | 2434             | 1920x1080 | 23.4 | 2010 | [B4619E858A39](<Digital/AOC/AOC2434/B4619E858A39>) |
| AOC              | AOC2434 | 2434             | 1920x1080 | 23.4 | 2009 | [222527910906](<Digital/AOC/AOC2434/222527910906>) |
| AOC              | AOC2436 | 2436             | 1920x1080 | 23.4 | 2011 | [191FEF02A717](<Digital/AOC/AOC2436/191FEF02A717>) |
| AOC              | AOC2436 | 2436             | 1920x1080 | 23.4 | 2010 | [58997FF01A62](<Digital/AOC/AOC2436/58997FF01A62>) |
| AOC              | AOC2436 | 2436             | 1920x1080 | 23.4 | 2009 | [3B66B7BCEB7E](<Digital/AOC/AOC2436/3B66B7BCEB7E>) |
| AOC              | AOC2436 | 2436             | 1920x1080 | 23.4 |      | [14338850EB2B](<Digital/AOC/AOC2436/14338850EB2B>) |
| AOC              | AOC2437 | 2437             | 1920x1080 | 23.4 | 2011 | [6F974A735FAC](<Digital/AOC/AOC2437/6F974A735FAC>) |
| AOC              | AOC2437 | 2437             | 1920x1080 | 23.4 | 2010 | [1BCCB10FE6B5](<Digital/AOC/AOC2437/1BCCB10FE6B5>) |
| AOC              | AOC2440 | 2440             | 1920x1080 | 24.0 | 2011 | [30AF6F53CCF0](<Digital/AOC/AOC2440/30AF6F53CCF0>) |
| AOC              | AOC2440 | 2440             | 1920x1080 | 24.0 | 2010 | [B3443B0DEA86](<Digital/AOC/AOC2440/B3443B0DEA86>) |
| AOC              | AOC2442 | T2442e           | 1920x1080 | 21.7 | 2010 | [730C1AEE0182](<Digital/AOC/AOC2442/730C1AEE0182>) |
| AOC              | AOC2442 | T2442e           | 1920x1080 | 21.7 |      | [548DD9D9012C](<Digital/AOC/AOC2442/548DD9D9012C>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 | 2016 | [B51A227E1BC0](<Digital/AOC/AOC2450/B51A227E1BC0>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 | 2015 | [3A1829CEC280](<Digital/AOC/AOC2450/3A1829CEC280>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 | 2014 | [392A8A2A4ED8](<Digital/AOC/AOC2450/392A8A2A4ED8>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 | 2013 | [010D0FC726A3](<Digital/AOC/AOC2450/010D0FC726A3>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 | 2012 | [0322C0AFE221](<Digital/AOC/AOC2450/0322C0AFE221>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 | 2011 | [629DCC0E6B9B](<Digital/AOC/AOC2450/629DCC0E6B9B>) |
| AOC              | AOC2450 | 2450W            | 1920x1080 | 23.4 |      | [F0B9CE5746DC](<Digital/AOC/AOC2450/F0B9CE5746DC>) |
| AOC              | AOC2460 | 2460G4           | 1920x1080 | 24.0 | 2018 | [37D68C4C647D](<Digital/AOC/AOC2460/37D68C4C647D>) |
| AOC              | AOC2460 | 2460G4           | 1920x1080 | 24.0 | 2017 | [01CCD3951622](<Digital/AOC/AOC2460/01CCD3951622>) |
| AOC              | AOC2460 | 2460G5           | 1920x1080 | 24.0 | 2016 | [02A0E7D75545](<Digital/AOC/AOC2460/02A0E7D75545>) |
| AOC              | AOC2460 | 2460X            | 1920x1200 | 24.0 | 2016 | [BEE53C013E76](<Digital/AOC/AOC2460/BEE53C013E76>) |
| AOC              | AOC2460 | 2460G4           | 1920x1080 | 24.0 | 2015 | [0559CFCA5CE1](<Digital/AOC/AOC2460/0559CFCA5CE1>) |
| AOC              | AOC2460 | 2460X            | 1920x1200 | 24.0 | 2015 | [B0C318F7C324](<Digital/AOC/AOC2460/B0C318F7C324>) |
| AOC              | AOC2460 | 2460X            | 1920x1200 | 24.0 | 2014 | [077E3B06348E](<Digital/AOC/AOC2460/077E3B06348E>) |
| AOC              | AOC2460 | 2460             | 1920x1080 | 24.0 | 2014 | [26BFE4D8B597](<Digital/AOC/AOC2460/26BFE4D8B597>) |
| AOC              | AOC2460 | G2460            | 1920x1080 | 24.0 | 2013 | [236D98AA6C87](<Digital/AOC/AOC2460/236D98AA6C87>) |
| AOC              | AOC2460 | 2460X            | 1920x1200 | 24.0 | 2013 | [745C0AF9FED4](<Digital/AOC/AOC2460/745C0AF9FED4>) |
| AOC              | AOC2460 | 2460             | 1920x1080 | 24.0 | 2012 | [02F61FBF1697](<Digital/AOC/AOC2460/02F61FBF1697>) |
| AOC              | AOC2460 | 2460W            | 1920x1080 | 23.4 | 2012 | [9BB6A66954DB](<Digital/AOC/AOC2460/9BB6A66954DB>) |
| AOC              | AOC2460 | G2460            | 1920x1080 | 24.0 |      | [0E522925CDD1](<Digital/AOC/AOC2460/0E522925CDD1>) |
| AOC              | AOC2461 | 2460G4           | 1920x1080 | 24.0 | 2016 | [76157FF4A79B](<Digital/AOC/AOC2461/76157FF4A79B>) |
| AOC              | AOC2461 | 2461W            | 1920x1080 | 23.4 | 2014 | [1C76F1AE02C8](<Digital/AOC/AOC2461/1C76F1AE02C8>) |
| AOC              | AOC2461 | 2461W            | 1920x1080 | 23.4 | 2013 | [138D6CBBA465](<Digital/AOC/AOC2461/138D6CBBA465>) |
| AOC              | AOC2461 | 2461W            | 1920x1080 | 23.4 | 2012 | [092B97B057AA](<Digital/AOC/AOC2461/092B97B057AA>) |
| AOC              | AOC2461 | 2461W            | 1920x1080 | 23.4 |      | [2A670D242B15](<Digital/AOC/AOC2461/2A670D242B15>) |
| AOC              | AOC2462 | 2462w            | 1920x1080 | 23.4 | 2013 | [22E9D5013316](<Digital/AOC/AOC2462/22E9D5013316>) |
| AOC              | AOC2462 | 2462w            | 1920x1080 | 23.4 |      | [F1F1DFDCB590](<Digital/AOC/AOC2462/F1F1DFDCB590>) |
| AOC              | AOC246A | 2460G5           | 1920x1080 | 24.0 | 2021 | [7AF869592E79](<Digital/AOC/AOC246A/7AF869592E79>) |
| AOC              | AOC246A | 2460G5           | 1920x1080 | 24.0 | 2020 | [124B20406FB4](<Digital/AOC/AOC246A/124B20406FB4>) |
| AOC              | AOC246A | 2460G5           | 1920x1080 | 24.0 | 2019 | [0392896B4949](<Digital/AOC/AOC246A/0392896B4949>) |
| AOC              | AOC246A | G2460            | 1920x1080 | 24.0 | 2018 | [0276BD74A2BE](<Digital/AOC/AOC246A/0276BD74A2BE>) |
| AOC              | AOC246A | 2460X            | 1920x1200 | 24.0 | 2018 | [477A8E7EDD04](<Digital/AOC/AOC246A/477A8E7EDD04>) |
| AOC              | AOC246A | 2460             | 1920x1080 | 24.0 | 2017 | [053D06C88F7A](<Digital/AOC/AOC246A/053D06C88F7A>) |
| AOC              | AOC246A | 2460X            | 1920x1200 | 24.0 | 2017 | [49D6A2BD5683](<Digital/AOC/AOC246A/49D6A2BD5683>) |
| AOC              | AOC246A | G2460            | 1920x1080 | 24.0 |      | [01057135746C](<Digital/AOC/AOC246A/01057135746C>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2024 | [7249CEED566E](<Digital/AOC/AOC2470/7249CEED566E>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2023 | [4883F272CB01](<Digital/AOC/AOC2470/4883F272CB01>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2022 | [0CE7B6FD4CB2](<Digital/AOC/AOC2470/0CE7B6FD4CB2>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2021 | [0AC6E4F2006D](<Digital/AOC/AOC2470/0AC6E4F2006D>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2020 | [02BA8DECCD7A](<Digital/AOC/AOC2470/02BA8DECCD7A>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2019 | [034C1D58753A](<Digital/AOC/AOC2470/034C1D58753A>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2018 | [00B25BC739D9](<Digital/AOC/AOC2470/00B25BC739D9>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2017 | [0017B39FEBAE](<Digital/AOC/AOC2470/0017B39FEBAE>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2016 | [0733BA2A625F](<Digital/AOC/AOC2470/0733BA2A625F>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2015 | [03A945D2FA94](<Digital/AOC/AOC2470/03A945D2FA94>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2014 | [255D3EF98809](<Digital/AOC/AOC2470/255D3EF98809>) |
| AOC              | AOC2470 | 2470W1M          | 1920x1080 | 24.0 | 2014 | [7A0081BAF1EB](<Digital/AOC/AOC2470/7A0081BAF1EB>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 | 2013 | [431257189C2B](<Digital/AOC/AOC2470/431257189C2B>) |
| AOC              | AOC2470 | 2470W1M          | 1920x1080 | 24.0 | 2013 | [6E958E316C2F](<Digital/AOC/AOC2470/6E958E316C2F>) |
| AOC              | AOC2470 | 2470W            | 1920x1080 | 23.4 |      | [1AE1BBC27110](<Digital/AOC/AOC2470/1AE1BBC27110>) |
| AOC              | AOC2471 | 2471M            | 1920x1080 | 24.0 | 2013 | [58D6B8516F4B](<Digital/AOC/AOC2471/58D6B8516F4B>) |
| AOC              | AOC2472 | 2472WM           | 1920x1080 | 23.4 | 2014 | [5FFB50D9D4F0](<Digital/AOC/AOC2472/5FFB50D9D4F0>) |
| AOC              | AOC2473 | 2473W1M          | 1920x1080 | 24.0 | 2014 | [1061242DFE7B](<Digital/AOC/AOC2473/1061242DFE7B>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 23.4 | 2020 | [222B635E43B8](<Digital/AOC/AOC2475/222B635E43B8>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 23.4 | 2019 | [65837D1E4B12](<Digital/AOC/AOC2475/65837D1E4B12>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 23.4 | 2018 | [10353C366A30](<Digital/AOC/AOC2475/10353C366A30>) |
| AOC              | AOC2475 | 2475W1           | 1920x1080 | 24.0 | 2018 | [3B0B6E86616E](<Digital/AOC/AOC2475/3B0B6E86616E>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 24.0 | 2017 | [0028EF5C749A](<Digital/AOC/AOC2475/0028EF5C749A>) |
| AOC              | AOC2475 | 2475WR           | 1920x1200 | 24.0 | 2017 | [965BB91540D4](<Digital/AOC/AOC2475/965BB91540D4>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 23.4 | 2017 | [CAEA52DACF48](<Digital/AOC/AOC2475/CAEA52DACF48>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 23.4 | 2016 | [0FB5A8A9733C](<Digital/AOC/AOC2475/0FB5A8A9733C>) |
| AOC              | AOC2475 | 2475W1           | 1920x1080 | 24.0 | 2016 | [3B80CC9482DB](<Digital/AOC/AOC2475/3B80CC9482DB>) |
| AOC              | AOC2475 | 2475WR           | 1920x1200 | 24.0 | 2016 | [C272752A0C4D](<Digital/AOC/AOC2475/C272752A0C4D>) |
| AOC              | AOC2475 | 2475W1           | 1920x1080 | 24.0 | 2015 | [1BA2CF428C9D](<Digital/AOC/AOC2475/1BA2CF428C9D>) |
| AOC              | AOC2475 | 2475W            | 1920x1080 | 23.4 |      | [28CF7DCE3B3C](<Digital/AOC/AOC2475/28CF7DCE3B3C>) |
| AOC              | AOC2476 | 2476WM           | 1920x1080 | 23.4 | 2017 | [090297A3906F](<Digital/AOC/AOC2476/090297A3906F>) |
| AOC              | AOC2476 | 2476WM           | 1920x1080 | 23.4 | 2016 | [083C8E3500B0](<Digital/AOC/AOC2476/083C8E3500B0>) |
| AOC              | AOC2476 | 2476WM           | 1920x1080 | 23.4 | 2015 | [21844229A3D7](<Digital/AOC/AOC2476/21844229A3D7>) |
| AOC              | AOC2476 | 2476WM           | 1920x1080 | 23.4 | 2014 | [12902DBC9AAD](<Digital/AOC/AOC2476/12902DBC9AAD>) |
| AOC              | AOC2477 | 2477W1M          | 1920x1080 | 24.0 | 2017 | [AB6342902DE4](<Digital/AOC/AOC2477/AB6342902DE4>) |
| AOC              | AOC2477 | Q2477W1          | 2560x1440 | 23.6 | 2017 | [FB76F5EB0CE2](<Digital/AOC/AOC2477/FB76F5EB0CE2>) |
| AOC              | AOC2477 | U2477WM          | 3840x2160 | 23.4 | 2016 | [BDF7FDCAAA36](<Digital/AOC/AOC2477/BDF7FDCAAA36>) |
| AOC              | AOC2477 | 2477W1M          | 1920x1080 | 24.0 | 2015 | [C2D7E3A64013](<Digital/AOC/AOC2477/C2D7E3A64013>) |
| AOC              | AOC2479 | 2479W1           | 1920x1080 | 24.0 | 2009 | [0641C2B0970F](<Digital/AOC/AOC2479/0641C2B0970F>) |
| AOC              | AOC2480 | 2480W1           | 1920x1080 | 24.0 | 2020 | [3D6021D21E9D](<Digital/AOC/AOC2480/3D6021D21E9D>) |
| AOC              | AOC2480 | 2480W1           | 1920x1080 | 24.0 | 2019 | [80767E1C47A0](<Digital/AOC/AOC2480/80767E1C47A0>) |
| AOC              | AOC2480 | 2480W1           | 1920x1080 | 24.0 | 2018 | [E4D415F35974](<Digital/AOC/AOC2480/E4D415F35974>) |
| AOC              | AOC2480 | 2480W1           | 1920x1080 | 24.0 | 2017 | [06FEFBC08A7C](<Digital/AOC/AOC2480/06FEFBC08A7C>) |
| AOC              | AOC2481 | 2481W            | 1920x1080 | 24.0 | 2020 | [057AC6DD19C5](<Digital/AOC/AOC2481/057AC6DD19C5>) |
| AOC              | AOC2481 | 2481W            | 1920x1080 | 24.0 | 2019 | [387DD412544F](<Digital/AOC/AOC2481/387DD412544F>) |
| AOC              | AOC2481 | 2481W            | 1920x1080 | 24.0 | 2018 | [05BDD2C8B7C2](<Digital/AOC/AOC2481/05BDD2C8B7C2>) |
| AOC              | AOC2481 | 2481W            | 1920x1080 | 24.0 | 2017 | [29FDA442008B](<Digital/AOC/AOC2481/29FDA442008B>) |
| AOC              | AOC2481 | 2481W            | 1920x1080 | 24.0 | 2016 | [05E5085B441F](<Digital/AOC/AOC2481/05E5085B441F>) |
| AOC              | AOC2481 | 2481W            | 1920x1080 | 24.0 |      | [91A23FAB91EB](<Digital/AOC/AOC2481/91A23FAB91EB>) |
| AOC              | AOC2489 | 2489W1           | 1920x1080 | 24.0 | 2017 | [B59CBE4327BC](<Digital/AOC/AOC2489/B59CBE4327BC>) |
| AOC              | AOC2490 | G2490W1G4        | 1920x1080 | 24.0 | 2024 | [81A8B62FDDFD](<Digital/AOC/AOC2490/81A8B62FDDFD>) |
| AOC              | AOC2490 | G2490W1G4        | 1920x1080 | 24.0 | 2022 | [4361FE41FE75](<Digital/AOC/AOC2490/4361FE41FE75>) |
| AOC              | AOC2490 | 2490W1           | 1920x1080 | 24.0 | 2021 | [05310DED1D6C](<Digital/AOC/AOC2490/05310DED1D6C>) |
| AOC              | AOC2490 | G2490W1G4        | 1920x1080 | 24.0 | 2020 | [01BF1519F1CD](<Digital/AOC/AOC2490/01BF1519F1CD>) |
| AOC              | AOC2490 | 2490W1           | 1920x1080 | 24.0 | 2019 | [0771039E6394](<Digital/AOC/AOC2490/0771039E6394>) |
| AOC              | AOC2490 | Q2490W1          | 2560x1440 | 24.0 | 2019 | [80F5777CE010](<Digital/AOC/AOC2490/80F5777CE010>) |
| AOC              | AOC2490 | 2490W1           | 1920x1080 | 24.0 | 2018 | [1BC594AC202D](<Digital/AOC/AOC2490/1BC594AC202D>) |
| AOC              | AOC2490 | 2490W1           | 1920x1080 | 24.0 | 2017 | [08E3440C391B](<Digital/AOC/AOC2490/08E3440C391B>) |
| AOC              | AOC2490 | 2490W1           | 1920x1080 | 24.0 |      | [032D496B903E](<Digital/AOC/AOC2490/032D496B903E>) |
| AOC              | AOC2491 | 2491W            | 1920x1080 | 23.4 | 2019 | [AA3CD7B43300](<Digital/AOC/AOC2491/AA3CD7B43300>) |
| AOC              | AOC2491 | 2491W            | 1920x1080 | 23.4 | 2017 | [13A5F491033B](<Digital/AOC/AOC2491/13A5F491033B>) |
| AOC              | AOC2495 | 2495             | 1920x1080 | 24.0 | 2015 | [878EF20A5F83](<Digital/AOC/AOC2495/878EF20A5F83>) |
| AOC              | AOC2495 | 2495             | 1920x1080 | 24.0 | 2014 | [31F68AD2E099](<Digital/AOC/AOC2495/31F68AD2E099>) |
| AOC              | AOC2495 | 2495             | 1920x1080 | 24.0 | 2013 | [5249F9688DB1](<Digital/AOC/AOC2495/5249F9688DB1>) |
| AOC              | AOC2495 | 2495             | 1920x1080 | 24.0 | 2012 | [A6512C05D41F](<Digital/AOC/AOC2495/A6512C05D41F>) |
| AOC              | AOC2510 | AG251F1WG2       | 1920x1080 | 24.3 | 2021 | [A1392B70838E](<Digital/AOC/AOC2510/A1392B70838E>) |
| AOC              | AOC2510 | AG251F1WG2       | 1920x1080 | 24.3 | 2020 | [C88613FF0DBB](<Digital/AOC/AOC2510/C88613FF0DBB>) |
| AOC              | AOC2510 | AG251FWG2        | 1920x1080 | 24.3 | 2019 | [7A309AC70316](<Digital/AOC/AOC2510/7A309AC70316>) |
| AOC              | AOC2510 | AG251FWG2        | 1920x1080 | 24.3 | 2018 | [88B58B50AF78](<Digital/AOC/AOC2510/88B58B50AF78>) |
| AOC              | AOC2510 | AG251FWG2        | 1920x1080 | 24.3 | 2017 | [108F9419906A](<Digital/AOC/AOC2510/108F9419906A>) |
| AOC              | AOC2510 | AG251FWG2        | 1920x1080 | 24.3 |      | [37833D5D3B21](<Digital/AOC/AOC2510/37833D5D3B21>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 | 2020 | [111663F22F89](<Digital/AOC/AOC2577/111663F22F89>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 | 2019 | [E02B1CA7BE1C](<Digital/AOC/AOC2577/E02B1CA7BE1C>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 | 2018 | [36F5C2839FCF](<Digital/AOC/AOC2577/36F5C2839FCF>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 | 2017 | [1C5D5305E817](<Digital/AOC/AOC2577/1C5D5305E817>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 | 2016 | [0B53FF75D325](<Digital/AOC/AOC2577/0B53FF75D325>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 | 2015 | [CBABF37BC75F](<Digital/AOC/AOC2577/CBABF37BC75F>) |
| AOC              | AOC2577 | Q2577W           | 2560x1440 | 24.9 |      | [CF6D29BC3D3F](<Digital/AOC/AOC2577/CF6D29BC3D3F>) |
| AOC              | AOC2590 | 2590G5           | 1920x1080 | 24.3 | 2021 | [24512CCD0580](<Digital/AOC/AOC2590/24512CCD0580>) |
| AOC              | AOC2590 | 2590G4           | 1920x1080 | 24.3 | 2020 | [1629C3309ABF](<Digital/AOC/AOC2590/1629C3309ABF>) |
| AOC              | AOC2590 | 2590G4           | 1920x1080 | 24.3 | 2019 | [0A1E98C2D731](<Digital/AOC/AOC2590/0A1E98C2D731>) |
| AOC              | AOC2590 | 2590G4           | 1920x1080 | 24.3 | 2018 | [0943D21BA117](<Digital/AOC/AOC2590/0943D21BA117>) |
| AOC              | AOC2590 | 2590G4           | 1920x1080 | 24.3 |      | [24BB3DA086C8](<Digital/AOC/AOC2590/24BB3DA086C8>) |
| AOC              | AOC2615 | LE26W154         | 1360x768  | 26.1 | 2011 | [1438E5780CBE](<Digital/AOC/AOC2615/1438E5780CBE>) |
| AOC              | AOC2615 | LE26W154         | 1920x1080 | 26.1 |      | [93F2FCDAF80F](<Digital/AOC/AOC2615/93F2FCDAF80F>) |
| AOC              | AOC2632 | L26W831A         | 1360x768  | 26.1 | 2009 | [B9753B9D6D84](<Digital/AOC/AOC2632/B9753B9D6D84>) |
| AOC              | AOC2683 | L26W831          | 1280x720  | 19.1 | 2009 | [726E451B2797](<Digital/AOC/AOC2683/726E451B2797>) |
| AOC              | AOC2700 | 2700             | 1920x1080 | 27.2 | 2018 | [6865C5A0957F](<Digital/AOC/AOC2700/6865C5A0957F>) |
| AOC              | AOC2700 | 2770Vh1          | 1920x1080 | 27.2 | 2011 | [A15DCEAA58D3](<Digital/AOC/AOC2700/A15DCEAA58D3>) |
| AOC              | AOC2701 | 27B1G5           | 1920x1080 | 27.2 | 2024 | [A724F9DB7356](<Digital/AOC/AOC2701/A724F9DB7356>) |
| AOC              | AOC2701 | Q27T1G5          | 2560x1440 | 27.2 | 2023 | [0EEB155975AE](<Digital/AOC/AOC2701/0EEB155975AE>) |
| AOC              | AOC2701 | 27B1             | 1920x1080 | 27.2 | 2023 | [18010534F6E3](<Digital/AOC/AOC2701/18010534F6E3>) |
| AOC              | AOC2701 | Q27T1G5          | 2560x1440 | 27.2 | 2022 | [7B7CB5EF1C5B](<Digital/AOC/AOC2701/7B7CB5EF1C5B>) |
| AOC              | AOC2701 | 27B1G5           | 1920x1080 | 27.2 | 2022 | [8EEAFF5E3440](<Digital/AOC/AOC2701/8EEAFF5E3440>) |
| AOC              | AOC2701 | Q27P1B           | 2560x1440 | 27.2 | 2021 | [03676EB9B3C5](<Digital/AOC/AOC2701/03676EB9B3C5>) |
| AOC              | AOC2701 | 27P1             | 1920x1080 | 27.2 | 2021 | [097160C0208C](<Digital/AOC/AOC2701/097160C0208C>) |
| AOC              | AOC2701 | U2701B           | 3840x2160 | 27.2 | 2021 | [9280A116CC05](<Digital/AOC/AOC2701/9280A116CC05>) |
| AOC              | AOC2701 | 27G1G4           | 1920x1080 | 27.2 | 2020 | [016C2AD81B98](<Digital/AOC/AOC2701/016C2AD81B98>) |
| AOC              | AOC2701 | Q27T1G5          | 2560x1440 | 27.2 | 2020 | [033711C82ADE](<Digital/AOC/AOC2701/033711C82ADE>) |
| AOC              | AOC2701 | 27G1G4           | 1920x1080 | 27.2 | 2019 | [0233611BEE5F](<Digital/AOC/AOC2701/0233611BEE5F>) |
| AOC              | AOC2701 | Q27G1WG4         | 2560x1440 | 27.2 | 2019 | [0E44E7ED75A8](<Digital/AOC/AOC2701/0E44E7ED75A8>) |
| AOC              | AOC2701 | U2701B           | 3840x2160 | 27.2 | 2019 | [4A3F6539AF60](<Digital/AOC/AOC2701/4A3F6539AF60>) |
| AOC              | AOC2701 | 27B1             | 1920x1080 | 27.2 | 2018 | [0693CAB465EF](<Digital/AOC/AOC2701/0693CAB465EF>) |
| AOC              | AOC2701 | Q27P1B           | 2560x1440 | 27.2 | 2018 | [50507E824590](<Digital/AOC/AOC2701/50507E824590>) |
| AOC              | AOC2701 | Q27G1WG4         | 2560x1440 | 27.2 |      | [07819F5B3794](<Digital/AOC/AOC2701/07819F5B3794>) |
| AOC              | AOC2701 | 27B1             | 1920x1080 | 27.2 |      | [16C45595C85E](<Digital/AOC/AOC2701/16C45595C85E>) |
| AOC              | AOC2702 | 27G2G8           | 1920x1080 | 27.2 | 2025 | [96A42B2EC681](<Digital/AOC/AOC2702/96A42B2EC681>) |
| AOC              | AOC2702 | 27G2G8           | 1920x1080 | 27.2 | 2024 | [00B6F341A3AE](<Digital/AOC/AOC2702/00B6F341A3AE>) |
| AOC              | AOC2702 | Q27G2G3R3B       | 2560x1440 | 27.2 | 2024 | [09F543BFAD19](<Digital/AOC/AOC2702/09F543BFAD19>) |
| AOC              | AOC2702 | U27U2G6R4B       | 3840x2160 | 27.2 | 2023 | [008C1F6A67D0](<Digital/AOC/AOC2702/008C1F6A67D0>) |
| AOC              | AOC2702 | 27G2WG3-         | 1920x1080 | 27.2 | 2023 | [015101AF7997](<Digital/AOC/AOC2702/015101AF7997>) |
| AOC              | AOC2702 | Q27G2SG4         | 2560x1440 | 27.2 | 2023 | [0ABEF050AD18](<Digital/AOC/AOC2702/0ABEF050AD18>) |
| AOC              | AOC2702 | Q27G2WG4         | 2560x1440 | 27.2 | 2022 | [00741620566A](<Digital/AOC/AOC2702/00741620566A>) |
| AOC              | AOC2702 | 27G2G8           | 1920x1080 | 27.2 | 2022 | [046C7E7964E7](<Digital/AOC/AOC2702/046C7E7964E7>) |
| AOC              | AOC2702 | U27U2G6R4B       | 3840x2160 | 27.2 | 2022 | [197E7A14438E](<Digital/AOC/AOC2702/197E7A14438E>) |
| AOC              | AOC2702 | Q27G2G4          | 2560x1440 | 27.2 | 2021 | [00B035B28824](<Digital/AOC/AOC2702/00B035B28824>) |
| AOC              | AOC2702 | 27G2WG3-         | 1920x1080 | 27.2 | 2021 | [0217693E97C9](<Digital/AOC/AOC2702/0217693E97C9>) |
| AOC              | AOC2702 | U27P2G6B         | 3840x2160 | 27.2 | 2021 | [7920F3D1DA9B](<Digital/AOC/AOC2702/7920F3D1DA9B>) |
| AOC              | AOC2702 | 27G2G3           | 1920x1080 | 27.2 | 2020 | [016F4A82294D](<Digital/AOC/AOC2702/016F4A82294D>) |
| AOC              | AOC2702 | Q27G2WG4         | 2560x1440 | 27.2 | 2020 | [01C64328FAD3](<Digital/AOC/AOC2702/01C64328FAD3>) |
| AOC              | AOC2702 | U27P2G6B         | 3840x2160 | 27.2 | 2020 | [0DF33EBAD1CF](<Digital/AOC/AOC2702/0DF33EBAD1CF>) |
| AOC              | AOC2702 | 27G2G5           | 1920x1080 | 27.2 | 2019 | [0C6B70A532B1](<Digital/AOC/AOC2702/0C6B70A532B1>) |
| AOC              | AOC2702 | Q27G2WG4         | 2560x1440 | 27.2 | 2019 | [33E6BACEBFB7](<Digital/AOC/AOC2702/33E6BACEBFB7>) |
| AOC              | AOC2702 | 27V2G5           | 1920x1080 | 27.2 | 2018 | [44F6958F69F4](<Digital/AOC/AOC2702/44F6958F69F4>) |
| AOC              | AOC2702 | 27V2G5           | 1920x1080 | 27.2 |      | [47A524675836](<Digital/AOC/AOC2702/47A524675836>) |
| AOC              | AOC2702 | Q27G2G4          | 2560x1440 | 27.2 |      | [746C7FB7F2F6](<Digital/AOC/AOC2702/746C7FB7F2F6>) |
| AOC              | AOC2703 | 27B31H           | 1920x1080 | 27.2 | 2025 | [19ABE064FDF8](<Digital/AOC/AOC2703/19ABE064FDF8>) |
| AOC              | AOC2703 | Q27B3MA          | 2560x1440 | 27.2 | 2024 | [001EF517A435](<Digital/AOC/AOC2703/001EF517A435>) |
| AOC              | AOC2703 | U27B3AF          | 3840x2160 | 27.2 | 2024 | [3D1EE3EF84A0](<Digital/AOC/AOC2703/3D1EE3EF84A0>) |
| AOC              | AOC2703 | 27B3HA2          | 1920x1080 | 27.2 | 2024 | [44979B067521](<Digital/AOC/AOC2703/44979B067521>) |
| AOC              | AOC2703 | Q27B3MA          | 2560x1440 | 27.2 | 2023 | [2AA3BC2DCF06](<Digital/AOC/AOC2703/2AA3BC2DCF06>) |
| AOC              | AOC2703 | 27B3HM           | 1920x1080 | 27.2 | 2023 | [72171E0BC5C9](<Digital/AOC/AOC2703/72171E0BC5C9>) |
| AOC              | AOC2703 | U27N3R           | 3840x2160 | 27.2 | 2023 | [DE9EB476FD3E](<Digital/AOC/AOC2703/DE9EB476FD3E>) |
| AOC              | AOC2703 | Q27B3MA          | 2560x1440 | 27.2 | 2022 | [0F07C7B32ADC](<Digital/AOC/AOC2703/0F07C7B32ADC>) |
| AOC              | AOC2703 | U27N3G6R4B       | 3840x2160 | 27.2 | 2022 | [DF2A54070773](<Digital/AOC/AOC2703/DF2A54070773>) |
| AOC              | AOC2703 | U27N3G6R4B       | 3840x2160 | 27.2 | 2021 | [3888BB8DAA4D](<Digital/AOC/AOC2703/3888BB8DAA4D>) |
| AOC              | AOC2703 | Q27N3G5R4        | 2560x1440 | 27.2 | 2021 | [B703132D4E67](<Digital/AOC/AOC2703/B703132D4E67>) |
| AOC              | AOC2703 | 27N3G5           | 1920x1080 | 27.2 | 2021 | [E9AD23CEC0B2](<Digital/AOC/AOC2703/E9AD23CEC0B2>) |
| AOC              | AOC2703 | 27V3             | 1920x1080 | 27.2 | 2020 | [58CBADF33FE6](<Digital/AOC/AOC2703/58CBADF33FE6>) |
| AOC              | AOC2703 | U27V3B           | 3840x2160 | 27.2 | 2019 | [8256095D2FCC](<Digital/AOC/AOC2703/8256095D2FCC>) |
| AOC              | AOC2704 | Q27V4G5          | 2560x1440 | 27.2 | 2023 | [4D22DCED017A](<Digital/AOC/AOC2704/4D22DCED017A>) |
| AOC              | AOC2704 | U27V4G6B         | 3840x2160 | 27.2 | 2023 | [E9CE799E3844](<Digital/AOC/AOC2704/E9CE799E3844>) |
| AOC              | AOC2704 | Q27V4G5          | 2560x1440 | 27.2 | 2022 | [19BB13549FBA](<Digital/AOC/AOC2704/19BB13549FBA>) |
| AOC              | AOC2704 | U27V4G6B         | 3840x2160 | 27.2 | 2021 | [6449178828A0](<Digital/AOC/AOC2704/6449178828A0>) |
| AOC              | AOC2704 | Q27V4G5          | 2560x1440 | 27.2 | 2021 | [C2433639192E](<Digital/AOC/AOC2704/C2433639192E>) |
| AOC              | AOC2704 | 27G2G3           | 1920x1080 | 27.2 | 2020 | [C74874F78C19](<Digital/AOC/AOC2704/C74874F78C19>) |
| AOC              | AOC2710 | Q27G10ZE         | 2560x1440 | 27.2 | 2024 | [B40D492E7C58](<Digital/AOC/AOC2710/B40D492E7C58>) |
| AOC              | AOC2710 | AG271F1G2        | 1920x1080 | 27.2 | 2020 | [27EB30BBF98B](<Digital/AOC/AOC2710/27EB30BBF98B>) |
| AOC              | AOC2710 | AG271QG4         | 2560x1440 | 27.2 | 2019 | [3EC06B59EAAD](<Digital/AOC/AOC2710/3EC06B59EAAD>) |
| AOC              | AOC2710 | AG271F1G2        | 1920x1080 | 24.3 | 2019 | [B68FCAAE755A](<Digital/AOC/AOC2710/B68FCAAE755A>) |
| AOC              | AOC2710 | AG271QG4         | 2560x1440 | 27.2 | 2018 | [062CACF6879D](<Digital/AOC/AOC2710/062CACF6879D>) |
| AOC              | AOC2710 | AG271QG4         | 2560x1440 | 27.2 | 2017 | [177B7102A479](<Digital/AOC/AOC2710/177B7102A479>) |
| AOC              | AOC2710 | PD271F           | 1920x1080 | 27.2 | 2017 | [A5103437345E](<Digital/AOC/AOC2710/A5103437345E>) |
| AOC              | AOC2710 | AG271QG4         | 2560x1440 | 27.2 | 2016 | [3DC0DC67BC3D](<Digital/AOC/AOC2710/3DC0DC67BC3D>) |
| AOC              | AOC2710 | AG271QG4         | 2560x1440 | 27.2 |      | [0CBC2B439AD0](<Digital/AOC/AOC2710/0CBC2B439AD0>) |
| AOC              | AOC2713 | AG271QG          | 2560x1440 | 27.2 | 2016 | [73B0D141B68A](<Digital/AOC/AOC2713/73B0D141B68A>) |
| AOC              | AOC2713 | AG271QG          | 2560x1440 | 27.2 |      | [038031831C7A](<Digital/AOC/AOC2713/038031831C7A>) |
| AOC              | AOC2716 | AG271UG          | 3840x2160 | 27.2 |      | [281114733F05](<Digital/AOC/AOC2716/281114733F05>) |
| AOC              | AOC2720 | AG272FG4         | 1920x1080 | 27.2 | 2018 | [7F71B93982C3](<Digital/AOC/AOC2720/7F71B93982C3>) |
| AOC              | AOC2720 | AG272QG4         | 2560x1440 | 27.2 | 2018 | [BAB3A807A9E1](<Digital/AOC/AOC2720/BAB3A807A9E1>) |
| AOC              | AOC2720 | AG272FG4         | 1920x1080 | 27.2 | 2017 | [001CC0978251](<Digital/AOC/AOC2720/001CC0978251>) |
| AOC              | AOC2727 | 2727             | 1920x1080 | 27.2 | 2016 | [74BE8B27ACF4](<Digital/AOC/AOC2727/74BE8B27ACF4>) |
| AOC              | AOC2727 | 2727             | 1920x1080 | 27.2 | 2015 | [2A223E2F5F2A](<Digital/AOC/AOC2727/2A223E2F5F2A>) |
| AOC              | AOC2730 | AG273QS3R4       | 2560x1440 | 27.2 | 2022 | [28CB89DC355B](<Digital/AOC/AOC2730/28CB89DC355B>) |
| AOC              | AOC2730 | AG273QG3R3B      | 2560x1440 | 27.2 | 2021 | [1727BB42DFFA](<Digital/AOC/AOC2730/1727BB42DFFA>) |
| AOC              | AOC2730 | AG273QS4R4       | 2560x1440 | 27.2 | 2020 | [0A185AAABF5B](<Digital/AOC/AOC2730/0A185AAABF5B>) |
| AOC              | AOC2730 | AG273QS3R4       | 2560x1440 | 27.2 | 2019 | [2823FF6169FC](<Digital/AOC/AOC2730/2823FF6169FC>) |
| AOC              | AOC2730 | AG273QS4R4       | 2560x1440 | 27.2 | 2018 | [660D3BED4C7F](<Digital/AOC/AOC2730/660D3BED4C7F>) |
| AOC              | AOC2738 | AG273QCG         | 2560x1440 | 27.7 |      | [33283F7344F1](<Digital/AOC/AOC2738/33283F7344F1>) |
| AOC              | AOC2752 | 2752H            | 1920x1080 | 27.2 | 2016 | [18583A94BDC1](<Digital/AOC/AOC2752/18583A94BDC1>) |
| AOC              | AOC2752 | 2752             | 1920x1080 | 26.5 | 2016 | [E06E6014045F](<Digital/AOC/AOC2752/E06E6014045F>) |
| AOC              | AOC2752 | 2752H            | 1920x1080 | 27.2 | 2015 | [103A4626840D](<Digital/AOC/AOC2752/103A4626840D>) |
| AOC              | AOC2752 | 2752             | 1920x1080 | 26.5 | 2015 | [2988C5B962CC](<Digital/AOC/AOC2752/2988C5B962CC>) |
| AOC              | AOC2752 | 2752H            | 1920x1080 | 27.2 | 2014 | [18F0E4A00E31](<Digital/AOC/AOC2752/18F0E4A00E31>) |
| AOC              | AOC2752 | 2752             | 1920x1080 | 26.5 | 2014 | [2561D2A1731C](<Digital/AOC/AOC2752/2561D2A1731C>) |
| AOC              | AOC2752 | 2752             | 1920x1080 | 26.5 | 2013 | [1E39D5AA8B8F](<Digital/AOC/AOC2752/1E39D5AA8B8F>) |
| AOC              | AOC2752 | e2752Vq          | 1920x1080 | 27.2 | 2013 | [22C6ABF75FEB](<Digital/AOC/AOC2752/22C6ABF75FEB>) |
| AOC              | AOC2752 | 2752             | 1920x1080 | 26.5 | 2012 | [204C4571BF12](<Digital/AOC/AOC2752/204C4571BF12>) |
| AOC              | AOC2752 | e2752Vq          | 1920x1080 | 27.2 | 2012 | [2A46C381557D](<Digital/AOC/AOC2752/2A46C381557D>) |
| AOC              | AOC2752 | 2752H            | 1920x1080 | 27.2 |      | [14CD9A2590D3](<Digital/AOC/AOC2752/14CD9A2590D3>) |
| AOC              | AOC2752 | 2752             | 1920x1080 | 26.5 |      | [43582509D79A](<Digital/AOC/AOC2752/43582509D79A>) |
| AOC              | AOC2757 | 2757             | 1920x1080 | 27.2 | 2016 | [03F3A99B0A49](<Digital/AOC/AOC2757/03F3A99B0A49>) |
| AOC              | AOC2757 | 2757M            | 1920x1080 | 27.2 | 2015 | [06AF6B2E23C0](<Digital/AOC/AOC2757/06AF6B2E23C0>) |
| AOC              | AOC2757 | 2757M            | 1920x1080 | 27.2 | 2014 | [0C3BBC6FD8C2](<Digital/AOC/AOC2757/0C3BBC6FD8C2>) |
| AOC              | AOC2757 | 2757             | 1920x1080 | 27.2 | 2013 | [04D569662102](<Digital/AOC/AOC2757/04D569662102>) |
| AOC              | AOC2757 | 2757M            | 1920x1080 | 27.2 | 2012 | [089D95833D43](<Digital/AOC/AOC2757/089D95833D43>) |
| AOC              | AOC2769 | 2769             | 1920x1080 | 27.2 | 2018 | [04AA4ABBE033](<Digital/AOC/AOC2769/04AA4ABBE033>) |
| AOC              | AOC2769 | 2769M            | 1920x1080 | 27.2 | 2017 | [1371F3E69849](<Digital/AOC/AOC2769/1371F3E69849>) |
| AOC              | AOC2769 | 2769M            | 1920x1080 | 27.2 | 2016 | [069D6E61B518](<Digital/AOC/AOC2769/069D6E61B518>) |
| AOC              | AOC2769 | 2769M            | 1920x1080 | 27.2 | 2015 | [05CD5C80F301](<Digital/AOC/AOC2769/05CD5C80F301>) |
| AOC              | AOC2769 | 2769M            | 1920x1080 | 27.2 | 2014 | [09FF47761A3C](<Digital/AOC/AOC2769/09FF47761A3C>) |
| AOC              | AOC2769 | 2769M            | 1920x1080 | 27.2 | 2013 | [338C953F116C](<Digital/AOC/AOC2769/338C953F116C>) |
| AOC              | AOC2769 | 2769M            | 1920x1080 | 27.2 |      | [14DE1E40EF40](<Digital/AOC/AOC2769/14DE1E40EF40>) |
| AOC              | AOC2770 | 2770             | 1920x1080 | 27.2 | 2018 | [12DA09C141F9](<Digital/AOC/AOC2770/12DA09C141F9>) |
| AOC              | AOC2770 | 2770G4           | 1920x1080 | 27.2 | 2017 | [07D3A531C433](<Digital/AOC/AOC2770/07D3A531C433>) |
| AOC              | AOC2770 | 2770             | 1920x1080 | 27.2 | 2016 | [0145E9022487](<Digital/AOC/AOC2770/0145E9022487>) |
| AOC              | AOC2770 | 2770G4           | 1920x1080 | 27.2 | 2015 | [002310B637A4](<Digital/AOC/AOC2770/002310B637A4>) |
| AOC              | AOC2770 | Q2770            | 2560x1440 | 27.2 | 2015 | [708A881117AD](<Digital/AOC/AOC2770/708A881117AD>) |
| AOC              | AOC2770 | 2770             | 1920x1080 | 27.2 | 2014 | [0B4400E21EE9](<Digital/AOC/AOC2770/0B4400E21EE9>) |
| AOC              | AOC2770 | Q2770            | 2560x1440 | 27.2 | 2014 | [1C071DE706B0](<Digital/AOC/AOC2770/1C071DE706B0>) |
| AOC              | AOC2770 | 2770             | 1920x1080 | 27.2 | 2013 | [286F13433DC1](<Digital/AOC/AOC2770/286F13433DC1>) |
| AOC              | AOC2770 | Q2770            | 2560x1440 | 27.2 | 2013 | [4CA2F81FFBFB](<Digital/AOC/AOC2770/4CA2F81FFBFB>) |
| AOC              | AOC2770 | 2770             | 1920x1080 | 27.2 |      | [17F4E829DACF](<Digital/AOC/AOC2770/17F4E829DACF>) |
| AOC              | AOC2770 | Q2770            | 2560x1440 | 27.2 |      | [BD684B8BD7FE](<Digital/AOC/AOC2770/BD684B8BD7FE>) |
| AOC              | AOC2775 | 2775             | 1920x1080 | 27.2 | 2019 | [78B8597ABE9B](<Digital/AOC/AOC2775/78B8597ABE9B>) |
| AOC              | AOC2775 | 2775             | 1920x1080 | 27.2 | 2018 | [01B6751AA75D](<Digital/AOC/AOC2775/01B6751AA75D>) |
| AOC              | AOC2775 | Q2775            | 2560x1440 | 27.2 | 2017 | [3EA9E6D17EAC](<Digital/AOC/AOC2775/3EA9E6D17EAC>) |
| AOC              | AOC2775 | 2775             | 1920x1080 | 27.2 | 2017 | [3FCA787960B1](<Digital/AOC/AOC2775/3FCA787960B1>) |
| AOC              | AOC2775 | 2775             | 1920x1080 | 27.2 | 2016 | [15220A35E756](<Digital/AOC/AOC2775/15220A35E756>) |
| AOC              | AOC2775 | Q2775            | 2560x1440 | 27.2 | 2016 | [4D5C7D18969E](<Digital/AOC/AOC2775/4D5C7D18969E>) |
| AOC              | AOC2777 | LV273HUPR        | 3840x2160 | 27.2 | 2021 | [D0EA1ADE451A](<Digital/AOC/AOC2777/D0EA1ADE451A>) |
| AOC              | AOC2777 | Q2777            | 2560x1440 | 27.2 | 2020 | [0D6E86967544](<Digital/AOC/AOC2777/0D6E86967544>) |
| AOC              | AOC2777 | LV273HUPR        | 3840x2160 | 27.2 | 2020 | [1F424DB50498](<Digital/AOC/AOC2777/1F424DB50498>) |
| AOC              | AOC2777 | U2777B           | 3840x2160 | 27.2 | 2019 | [097C9B7A45F8](<Digital/AOC/AOC2777/097C9B7A45F8>) |
| AOC              | AOC2777 | U2777B           | 3840x2160 | 27.2 | 2018 | [2755A10E9FCA](<Digital/AOC/AOC2777/2755A10E9FCA>) |
| AOC              | AOC2777 | U2777B           | 3840x2160 | 27.2 | 2017 | [5487C7A8ED98](<Digital/AOC/AOC2777/5487C7A8ED98>) |
| AOC              | AOC2777 | 2777M            | 1920x1080 | 27.2 | 2017 | [FA6A01F80A3E](<Digital/AOC/AOC2777/FA6A01F80A3E>) |
| AOC              | AOC2777 | U2777B           | 3840x2160 | 27.2 |      | [1B34D89B2322](<Digital/AOC/AOC2777/1B34D89B2322>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2020 | [CCC2B8EBC31B](<Digital/AOC/AOC2778/CCC2B8EBC31B>) |
| AOC              | AOC2778 | 2778G5           | 1920x1080 | 27.2 | 2020 | [DAFB91A5943F](<Digital/AOC/AOC2778/DAFB91A5943F>) |
| AOC              | AOC2778 | 2778G5           | 1920x1080 | 27.2 | 2019 | [60E6607ECEE1](<Digital/AOC/AOC2778/60E6607ECEE1>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2019 | [9D00D59AAE88](<Digital/AOC/AOC2778/9D00D59AAE88>) |
| AOC              | AOC2778 | 2778G5           | 1920x1080 | 27.2 | 2018 | [2120D72D5127](<Digital/AOC/AOC2778/2120D72D5127>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2018 | [26189F80E96A](<Digital/AOC/AOC2778/26189F80E96A>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2017 | [0C828322FA95](<Digital/AOC/AOC2778/0C828322FA95>) |
| AOC              | AOC2778 | 2778G5           | 1920x1080 | 27.2 | 2017 | [12E9A6C464BB](<Digital/AOC/AOC2778/12E9A6C464BB>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2016 | [01AE112A872E](<Digital/AOC/AOC2778/01AE112A872E>) |
| AOC              | AOC2778 | 2778G5           | 1920x1080 | 27.2 | 2016 | [2B54AEF44035](<Digital/AOC/AOC2778/2B54AEF44035>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2015 | [CDCD905A6176](<Digital/AOC/AOC2778/CDCD905A6176>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 | 2014 | [0FB260031923](<Digital/AOC/AOC2778/0FB260031923>) |
| AOC              | AOC2778 | 2778X            | 2560x1440 | 27.2 |      | [42542376E092](<Digital/AOC/AOC2778/42542376E092>) |
| AOC              | AOC2778 | 2778G5           | 1920x1080 | 27.2 |      | [5C26985EDC36](<Digital/AOC/AOC2778/5C26985EDC36>) |
| AOC              | AOC2779 | 2779             | 1920x1080 | 27.2 | 2019 | [2F4A51C2A3B4](<Digital/AOC/AOC2779/2F4A51C2A3B4>) |
| AOC              | AOC2779 | 2779             | 1920x1080 | 27.2 | 2018 | [536A536A0F1C](<Digital/AOC/AOC2779/536A536A0F1C>) |
| AOC              | AOC2779 | 2779             | 1920x1080 | 27.2 | 2017 | [63642B46C2AD](<Digital/AOC/AOC2779/63642B46C2AD>) |
| AOC              | AOC2779 | 2779             | 1920x1080 | 27.2 | 2016 | [371D49428671](<Digital/AOC/AOC2779/371D49428671>) |
| AOC              | AOC2779 | 2779             | 1920x1080 | 27.2 |      | [43802915D3D5](<Digital/AOC/AOC2779/43802915D3D5>) |
| AOC              | AOC2781 | 2781             | 1920x1080 | 27.2 | 2020 | [F09A13CC89AB](<Digital/AOC/AOC2781/F09A13CC89AB>) |
| AOC              | AOC2781 | 2781             | 1920x1080 | 27.2 | 2018 | [1AAA63F59D0D](<Digital/AOC/AOC2781/1AAA63F59D0D>) |
| AOC              | AOC2781 | Q2781            | 2560x1440 | 27.2 | 2018 | [3537AAB8CB5E](<Digital/AOC/AOC2781/3537AAB8CB5E>) |
| AOC              | AOC2781 | 2781             | 1920x1080 | 27.2 | 2017 | [072D2DE1BCB1](<Digital/AOC/AOC2781/072D2DE1BCB1>) |
| AOC              | AOC2781 | Q2781            | 2560x1440 | 27.2 | 2017 | [74B87C9F5FE3](<Digital/AOC/AOC2781/74B87C9F5FE3>) |
| AOC              | AOC2781 | 2781             | 1920x1080 | 27.2 | 2016 | [166555529C7E](<Digital/AOC/AOC2781/166555529C7E>) |
| AOC              | AOC2789 | Q2789            | 2560x1440 | 27.2 | 2019 | [FE7CC140CB8B](<Digital/AOC/AOC2789/FE7CC140CB8B>) |
| AOC              | AOC2789 | Q2789            | 2560x1440 | 27.2 | 2017 | [6375BBED812E](<Digital/AOC/AOC2789/6375BBED812E>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2024 | [B9A31AA5568F](<Digital/AOC/AOC2790/B9A31AA5568F>) |
| AOC              | AOC2790 | G2790G4          | 1920x1080 | 27.2 | 2023 | [6FB8D86B2AFE](<Digital/AOC/AOC2790/6FB8D86B2AFE>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2023 | [822D0BCFDEE9](<Digital/AOC/AOC2790/822D0BCFDEE9>) |
| AOC              | AOC2790 | G2790G4          | 1920x1080 | 27.2 | 2022 | [033466DF9484](<Digital/AOC/AOC2790/033466DF9484>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2022 | [5EA75A66A356](<Digital/AOC/AOC2790/5EA75A66A356>) |
| AOC              | AOC2790 | Q2790            | 2560x1440 | 27.2 | 2022 | [97BA1A7DE6B0](<Digital/AOC/AOC2790/97BA1A7DE6B0>) |
| AOC              | AOC2790 | Q2790            | 2560x1440 | 27.2 | 2021 | [001427DFC15E](<Digital/AOC/AOC2790/001427DFC15E>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2021 | [026B75B08050](<Digital/AOC/AOC2790/026B75B08050>) |
| AOC              | AOC2790 | G2790G4          | 1920x1080 | 27.2 | 2021 | [0433C311F7E1](<Digital/AOC/AOC2790/0433C311F7E1>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2020 | [05C26BE92CE8](<Digital/AOC/AOC2790/05C26BE92CE8>) |
| AOC              | AOC2790 | 2790G5           | 1920x1080 | 27.2 | 2020 | [05D09D3405BD](<Digital/AOC/AOC2790/05D09D3405BD>) |
| AOC              | AOC2790 | Q2790            | 2560x1440 | 27.2 | 2020 | [2A4B51364435](<Digital/AOC/AOC2790/2A4B51364435>) |
| AOC              | AOC2790 | Q2790            | 2560x1440 | 27.2 | 2019 | [00B95FBDC1CB](<Digital/AOC/AOC2790/00B95FBDC1CB>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2019 | [195DC8125275](<Digital/AOC/AOC2790/195DC8125275>) |
| AOC              | AOC2790 | 2790             | 1920x1080 | 27.2 | 2019 | [7D89C84D627E](<Digital/AOC/AOC2790/7D89C84D627E>) |
| AOC              | AOC2790 | Q2790            | 2560x1440 | 27.2 | 2018 | [0CC7E85D1DB4](<Digital/AOC/AOC2790/0CC7E85D1DB4>) |
| AOC              | AOC2790 | 2790WG5          | 1920x1080 | 27.2 | 2018 | [13FB0799F7AF](<Digital/AOC/AOC2790/13FB0799F7AF>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 | 2018 | [578F1BCCCCD4](<Digital/AOC/AOC2790/578F1BCCCCD4>) |
| AOC              | AOC2790 | 2790             | 1920x1080 | 27.2 | 2017 | [173A1FD8FB3D](<Digital/AOC/AOC2790/173A1FD8FB3D>) |
| AOC              | AOC2790 | 2790             | 1920x1080 | 27.2 |      | [03F786DE0E0D](<Digital/AOC/AOC2790/03F786DE0E0D>) |
| AOC              | AOC2790 | U2790B           | 3840x2160 | 27.2 |      | [4A978AAD8AA3](<Digital/AOC/AOC2790/4A978AAD8AA3>) |
| AOC              | AOC2790 | Q2790            | 2560x1440 | 27.2 |      | [79E9B9444012](<Digital/AOC/AOC2790/79E9B9444012>) |
| AOC              | AOC2791 | U2790B           | 3840x2160 | 27.2 | 2019 | [758485700C8B](<Digital/AOC/AOC2791/758485700C8B>) |
| AOC              | AOC2795 | 2795E            | 1920x1080 | 27.2 | 2012 | [12884395C7DE](<Digital/AOC/AOC2795/12884395C7DE>) |
| AOC              | AOC2795 | 2795E            | 1920x1080 | 27.2 | 2011 | [348B302D5975](<Digital/AOC/AOC2795/348B302D5975>) |
| AOC              | AOC2798 | 2798             | 1920x1080 | 27.2 | 2017 | [9723E88F885F](<Digital/AOC/AOC2798/9723E88F885F>) |
| AOC              | AOC2802 | U28G2G6B         | 3840x2160 | 27.8 | 2022 | [04773D6AA962](<Digital/AOC/AOC2802/04773D6AA962>) |
| AOC              | AOC2802 | U28P2G6B         | 3840x2160 | 27.8 | 2021 | [0AF76441E2BC](<Digital/AOC/AOC2802/0AF76441E2BC>) |
| AOC              | AOC2802 | U28G2G6B         | 3840x2160 | 27.8 | 2020 | [8C0838DA7FE3](<Digital/AOC/AOC2802/8C0838DA7FE3>) |
| AOC              | AOC2802 | U28G2E           | 3840x2160 | 27.8 |      | [951B4675D158](<Digital/AOC/AOC2802/951B4675D158>) |
| AOC              | AOC2868 | U2868G6R3B       | 3840x2160 | 27.8 | 2019 | [086E55615A35](<Digital/AOC/AOC2868/086E55615A35>) |
| AOC              | AOC2868 | U2868            | 3840x2160 | 27.8 | 2015 | [27AF6A676093](<Digital/AOC/AOC2868/27AF6A676093>) |
| AOC              | AOC2868 | U2868            | 3840x2160 | 27.8 | 2014 | [1FFD85A093A2](<Digital/AOC/AOC2868/1FFD85A093A2>) |
| AOC              | AOC2868 | U2868            | 3840x2160 | 27.8 |      | [B29D3DC50010](<Digital/AOC/AOC2868/B29D3DC50010>) |
| AOC              | AOC2870 | 2870             | 1920x1080 | 27.8 | 2016 | [6DCD37C4AF02](<Digital/AOC/AOC2870/6DCD37C4AF02>) |
| AOC              | AOC2870 | U2870            | 3840x2160 | 27.8 | 2015 | [3AE3616363FE](<Digital/AOC/AOC2870/3AE3616363FE>) |
| AOC              | AOC2870 | 2870             | 1920x1080 | 27.8 | 2015 | [94D6E663F853](<Digital/AOC/AOC2870/94D6E663F853>) |
| AOC              | AOC2870 | 2870             | 1920x1080 | 27.8 | 2014 | [5A4C073650F3](<Digital/AOC/AOC2870/5A4C073650F3>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2021 | [65D3884554BE](<Digital/AOC/AOC2879/65D3884554BE>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2020 | [013A01189120](<Digital/AOC/AOC2879/013A01189120>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2019 | [28E1C0E59140](<Digital/AOC/AOC2879/28E1C0E59140>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2018 | [188FABA677CD](<Digital/AOC/AOC2879/188FABA677CD>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2017 | [0896E6B1206E](<Digital/AOC/AOC2879/0896E6B1206E>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2016 | [05B976FEF3E7](<Digital/AOC/AOC2879/05B976FEF3E7>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 | 2015 | [C1B71F6984ED](<Digital/AOC/AOC2879/C1B71F6984ED>) |
| AOC              | AOC2879 | U2879G6          | 3840x2160 | 27.8 |      | [0566FFEB60DD](<Digital/AOC/AOC2879/0566FFEB60DD>) |
| AOC              | AOC2902 | Q29G2G5          | 2560x1080 | 29.1 | 2020 | [253440152922](<Digital/AOC/AOC2902/253440152922>) |
| AOC              | AOC2963 | Q2963            | 2560x1080 | 28.6 | 2017 | [0FD3A314E0FA](<Digital/AOC/AOC2963/0FD3A314E0FA>) |
| AOC              | AOC2963 | Q2963            | 2560x1080 | 28.6 | 2016 | [894FAB5DFC51](<Digital/AOC/AOC2963/894FAB5DFC51>) |
| AOC              | AOC2963 | 2963             | 2560x1080 | 28.6 | 2015 | [4A69EFCA19AB](<Digital/AOC/AOC2963/4A69EFCA19AB>) |
| AOC              | AOC2963 | 2963             | 2560x1080 | 28.6 | 2014 | [8A001CF8483A](<Digital/AOC/AOC2963/8A001CF8483A>) |
| AOC              | AOC2963 | 2963             | 2560x1080 | 28.6 | 2013 | [6C4C182C1127](<Digital/AOC/AOC2963/6C4C182C1127>) |
| AOC              | AOC3201 | Q32G1WG4         | 2560x1440 | 31.5 | 2021 | [0603D631A340](<Digital/AOC/AOC3201/0603D631A340>) |
| AOC              | AOC3201 | U32U1WR6B        | 3840x2160 | 31.5 | 2021 | [90D4FE724E03](<Digital/AOC/AOC3201/90D4FE724E03>) |
| AOC              | AOC3201 | 32G1WG4          | 1920x1080 | 31.5 | 2020 | [039B6A6188C3](<Digital/AOC/AOC3201/039B6A6188C3>) |
| AOC              | AOC3201 | Q32G1WG4         | 2560x1440 | 31.5 | 2020 | [0579596CBE14](<Digital/AOC/AOC3201/0579596CBE14>) |
| AOC              | AOC3201 | U32U1WR6B        | 3840x2160 | 31.5 | 2020 | [50B9F318F55F](<Digital/AOC/AOC3201/50B9F318F55F>) |
| AOC              | AOC3201 | Q32G1WG4         | 2560x1440 | 31.5 | 2019 | [0DDA8B81DFC2](<Digital/AOC/AOC3201/0DDA8B81DFC2>) |
| AOC              | AOC3201 | 32V1W            | 1920x1080 | 31.5 | 2019 | [0F53ADF41ED0](<Digital/AOC/AOC3201/0F53ADF41ED0>) |
| AOC              | AOC3201 | Q32G1WG4         | 2560x1440 | 31.5 | 2018 | [0D9A16539D3B](<Digital/AOC/AOC3201/0D9A16539D3B>) |
| AOC              | AOC3201 | 32G1WG4          | 1920x1080 | 31.5 | 2018 | [797FF82EE564](<Digital/AOC/AOC3201/797FF82EE564>) |
| AOC              | AOC3201 | U32U1WR6B        | 3840x2160 | 31.5 |      | [1263CC3FA0CF](<Digital/AOC/AOC3201/1263CC3FA0CF>) |
| AOC              | AOC3202 | Q32G2WG3         | 2560x1440 | 31.5 | 2024 | [63EB8897DB74](<Digital/AOC/AOC3202/63EB8897DB74>) |
| AOC              | AOC3202 | 32G2WG8          | 1920x1080 | 31.5 | 2024 | [6AA02A770757](<Digital/AOC/AOC3202/6AA02A770757>) |
| AOC              | AOC3202 | 32G2WG8          | 1920x1080 | 31.5 | 2023 | [0C0C4B163C8D](<Digital/AOC/AOC3202/0C0C4B163C8D>) |
| AOC              | AOC3202 | Q32G2WG3         | 2560x1440 | 31.5 | 2023 | [26D9C405D0D6](<Digital/AOC/AOC3202/26D9C405D0D6>) |
| AOC              | AOC3202 | U32P2WG6         | 3840x2160 | 31.5 | 2023 | [BBBB9BD97206](<Digital/AOC/AOC3202/BBBB9BD97206>) |
| AOC              | AOC3202 | Q32V3WG5         | 2560x1440 | 31.5 | 2022 | [015B5F58E86B](<Digital/AOC/AOC3202/015B5F58E86B>) |
| AOC              | AOC3202 | 32G2WG8          | 1920x1080 | 31.5 | 2022 | [0FDF1D6690ED](<Digital/AOC/AOC3202/0FDF1D6690ED>) |
| AOC              | AOC3202 | U32P2WG6         | 3840x2160 | 31.5 | 2022 | [B822172ADF62](<Digital/AOC/AOC3202/B822172ADF62>) |
| AOC              | AOC3202 | 32G2WG3          | 1920x1080 | 31.5 | 2021 | [07BA590D0D3D](<Digital/AOC/AOC3202/07BA590D0D3D>) |
| AOC              | AOC3202 | Q32P2WG5B        | 2560x1440 | 31.5 | 2021 | [0A9FC0C7DFE9](<Digital/AOC/AOC3202/0A9FC0C7DFE9>) |
| AOC              | AOC3202 | U32E2WG6         | 3840x2160 | 31.5 | 2021 | [11F3E48513B6](<Digital/AOC/AOC3202/11F3E48513B6>) |
| AOC              | AOC3202 | Q32G2WG4         | 2560x1440 | 31.5 | 2020 | [05A9757931E0](<Digital/AOC/AOC3202/05A9757931E0>) |
| AOC              | AOC3202 | 32G2WG3          | 1920x1080 | 31.5 | 2020 | [620C60A16ED8](<Digital/AOC/AOC3202/620C60A16ED8>) |
| AOC              | AOC3202 | U32N2W           | 3840x2160 | 31.5 | 2019 | [B753FCE7CD0F](<Digital/AOC/AOC3202/B753FCE7CD0F>) |
| AOC              | AOC3203 | U32V3            | 3840x2160 | 31.5 | 2021 | [8B70F5C2240E](<Digital/AOC/AOC3203/8B70F5C2240E>) |
| AOC              | AOC3203 | U32V3            | 3840x2160 | 31.5 | 2020 | [38627B1A71E0](<Digital/AOC/AOC3203/38627B1A71E0>) |
| AOC              | AOC3203 | Q32V3            | 2560x1440 | 31.5 | 2020 | [E5A502F930FA](<Digital/AOC/AOC3203/E5A502F930FA>) |
| AOC              | AOC3203 | LC32W033         | 1360x768  | 31.5 | 2010 | [C345D3A98BFE](<Digital/AOC/AOC3203/C345D3A98BFE>) |
| AOC              | AOC3203 | Q32V3            | 2560x1440 | 31.5 |      | [1520C684905B](<Digital/AOC/AOC3203/1520C684905B>) |
| AOC              | AOC3204 | Q32V4WG5         | 2560x1440 | 31.5 | 2024 | [2CA4F1B84CD0](<Digital/AOC/AOC3204/2CA4F1B84CD0>) |
| AOC              | AOC3204 | Q32V4WG5         | 2560x1440 | 31.5 | 2023 | [C50BF74EC5FE](<Digital/AOC/AOC3204/C50BF74EC5FE>) |
| AOC              | AOC3204 | Q32V4WG5         | 2560x1440 | 31.5 | 2022 | [13F73782AC12](<Digital/AOC/AOC3204/13F73782AC12>) |
| AOC              | AOC3205 | U32V5N           | 3840x2160 | 31.5 | 2024 | [0DEC5A26B262](<Digital/AOC/AOC3205/0DEC5A26B262>) |
| AOC              | AOC3207 | 3207W            | 1920x1080 | 31.5 | 2017 | [73085A209989](<Digital/AOC/AOC3207/73085A209989>) |
| AOC              | AOC3211 | Q32G11ZNE        | 2560x1440 | 31.5 | 2024 | [ACB761903374](<Digital/AOC/AOC3211/ACB761903374>) |
| AOC              | AOC3211 | LE32W157         | 1360x768  | 31.5 | 2011 | [5D4E9C58ED85](<Digital/AOC/AOC3211/5D4E9C58ED85>) |
| AOC              | AOC321A | L32W751A         | 1920x540  | 31.2 | 2008 | [49363949FA88](<Digital/AOC/AOC321A/49363949FA88>) |
| AOC              | AOC3220 | AG322QWS4R4      | 2560x1440 | 31.5 | 2020 | [2916F3846393](<Digital/AOC/AOC3220/2916F3846393>) |
| AOC              | AOC3220 | AG322FWG4        | 1920x1080 | 31.5 | 2020 | [D40D47524B64](<Digital/AOC/AOC3220/D40D47524B64>) |
| AOC              | AOC3220 | AG322QWS4R4      | 2560x1440 | 31.5 | 2019 | [3E4733B07D4E](<Digital/AOC/AOC3220/3E4733B07D4E>) |
| AOC              | AOC3220 | AG322QWS4R4      | 2560x1440 | 31.5 | 2018 | [1A195A241AB3](<Digital/AOC/AOC3220/1A195A241AB3>) |
| AOC              | AOC3220 | AG322FWG4        | 1920x1080 | 31.5 | 2018 | [1AD7DBBDCC8B](<Digital/AOC/AOC3220/1AD7DBBDCC8B>) |
| AOC              | AOC3220 | AG322FWG4        | 1920x1080 | 31.5 | 2017 | [05875C50C302](<Digital/AOC/AOC3220/05875C50C302>) |
| AOC              | AOC3220 | AG322QWG4        | 2560x1440 | 31.5 | 2017 | [47418670AFC2](<Digital/AOC/AOC3220/47418670AFC2>) |
| AOC              | AOC3220 | AG322FWG4        | 1920x1080 | 31.5 | 2016 | [0334D9A128B7](<Digital/AOC/AOC3220/0334D9A128B7>) |
| AOC              | AOC3220 | LE32D5520/20     | 1360x768  | 31.5 | 2011 | [4983FE084DAD](<Digital/AOC/AOC3220/4983FE084DAD>) |
| AOC              | AOC3220 | AG322QWS4R4      | 2560x1440 | 31.5 |      | [E764350CD031](<Digital/AOC/AOC3220/E764350CD031>) |
| AOC              | AOC3222 | LCD              | 1360x768  | 31.5 | 2012 | [6337B97F7485](<Digital/AOC/AOC3222/6337B97F7485>) |
| AOC              | AOC3230 | AG323FWG3R3      | 1920x1080 | 31.5 | 2024 | [FA5BEA038753](<Digital/AOC/AOC3230/FA5BEA038753>) |
| AOC              | AOC3230 | AG323FWG3R3      | 1920x1080 | 31.5 | 2023 | [10E89B64A198](<Digital/AOC/AOC3230/10E89B64A198>) |
| AOC              | AOC3230 | AG323FWG3R3      | 1920x1080 | 31.5 | 2022 | [2EFDAA255349](<Digital/AOC/AOC3230/2EFDAA255349>) |
| AOC              | AOC3230 | AG323FWG3R3      | 1920x1080 | 31.5 | 2021 | [00296D5B51ED](<Digital/AOC/AOC3230/00296D5B51ED>) |
| AOC              | AOC3230 | AG323QWG4R3+     | 2560x1440 | 31.5 | 2021 | [38A6F504317E](<Digital/AOC/AOC3230/38A6F504317E>) |
| AOC              | AOC3230 | AG323FWG3R3      | 1920x1080 | 31.5 | 2020 | [121448B06510](<Digital/AOC/AOC3230/121448B06510>) |
| AOC              | AOC3230 | AG323QWS4R4      | 2560x1440 | 31.5 | 2020 | [1BB8A494C662](<Digital/AOC/AOC3230/1BB8A494C662>) |
| AOC              | AOC3231 | D32W831          | 1360x768  | 31.2 | 2009 | [D5F625C13667](<Digital/AOC/AOC3231/D5F625C13667>) |
| AOC              | AOC3253 | LC32W053         | 1360x768  | 31.5 | 2010 | [4FBCE0B7EFD2](<Digital/AOC/AOC3253/4FBCE0B7EFD2>) |
| AOC              | AOC3258 | LE32H158I        | 1920x1080 | 31.5 | 2011 | [AF45E8E1A082](<Digital/AOC/AOC3258/AF45E8E1A082>) |
| AOC              | AOC3277 | U3277WB          | 3840x2160 | 31.5 | 2020 | [764AECC0D164](<Digital/AOC/AOC3277/764AECC0D164>) |
| AOC              | AOC3277 | Q3277            | 2560x1440 | 32.1 | 2020 | [A0C08881E8F6](<Digital/AOC/AOC3277/A0C08881E8F6>) |
| AOC              | AOC3277 | U3277WB          | 3840x2160 | 31.5 | 2019 | [00AAACDC892E](<Digital/AOC/AOC3277/00AAACDC892E>) |
| AOC              | AOC3277 | Q3277            | 2560x1440 | 32.1 | 2019 | [B490D6C60306](<Digital/AOC/AOC3277/B490D6C60306>) |
| AOC              | AOC3277 | U3277WB          | 3840x2160 | 31.5 | 2018 | [2145DCD924E3](<Digital/AOC/AOC3277/2145DCD924E3>) |
| AOC              | AOC3277 | Q3277            | 2560x1440 | 32.1 | 2018 | [4E56FDD8DE86](<Digital/AOC/AOC3277/4E56FDD8DE86>) |
| AOC              | AOC3277 | U3277WB          | 3840x2160 | 31.5 | 2017 | [0962FE5E3F05](<Digital/AOC/AOC3277/0962FE5E3F05>) |
| AOC              | AOC3277 | Q3277            | 2560x1440 | 32.1 | 2017 | [275219C1A4EC](<Digital/AOC/AOC3277/275219C1A4EC>) |
| AOC              | AOC3277 | U3277WB          | 3840x2160 | 31.5 | 2016 | [12DE1E751ACB](<Digital/AOC/AOC3277/12DE1E751ACB>) |
| AOC              | AOC3277 | Q3277            | 2560x1440 | 32.1 | 2016 | [16ABE685CDB6](<Digital/AOC/AOC3277/16ABE685CDB6>) |
| AOC              | AOC3277 | U3277            | 3840x2160 | 32.1 | 2015 | [22E3E4B78722](<Digital/AOC/AOC3277/22E3E4B78722>) |
| AOC              | AOC3277 | Q3277            | 2560x1440 | 32.1 | 2015 | [239082FE730E](<Digital/AOC/AOC3277/239082FE730E>) |
| AOC              | AOC3277 | U3277WB          | 3840x2160 | 31.5 |      | [2BF974BA513D](<Digital/AOC/AOC3277/2BF974BA513D>) |
| AOC              | AOC3279 | Q3279WG5B        | 2560x1440 | 33.4 | 2020 | [00A82E151235](<Digital/AOC/AOC3279/00A82E151235>) |
| AOC              | AOC3279 | Q3279WG5B        | 2560x1440 | 33.4 | 2019 | [007B1E426E2B](<Digital/AOC/AOC3279/007B1E426E2B>) |
| AOC              | AOC3279 | Q3279WG5B        | 2560x1440 | 33.4 | 2018 | [04314BCE2930](<Digital/AOC/AOC3279/04314BCE2930>) |
| AOC              | AOC3279 | Q3279WG5B        | 2560x1440 | 33.4 | 2017 | [0BA5C2F171BC](<Digital/AOC/AOC3279/0BA5C2F171BC>) |
| AOC              | AOC3279 | Q3279WG5B        | 2560x1440 | 33.4 |      | [1DCEA5A75455](<Digital/AOC/AOC3279/1DCEA5A75455>) |
| AOC              | AOC3288 | 3288W            | 1920x1080 | 31.5 | 2017 | [F6F4FF565927](<Digital/AOC/AOC3288/F6F4FF565927>) |
| AOC              | AOC3291 | L32HA91          | 1360x768  | 31.5 | 2010 | [7C802A403664](<Digital/AOC/AOC3291/7C802A403664>) |
| AOC              | AOC3293 | D32W931          | 1920x1080 | 31.5 |      | [4D4E21CEC2DA](<Digital/AOC/AOC3293/4D4E21CEC2DA>) |
| AOC              | AOC3296 | L32W961          | 1360x768  | 31.5 | 2009 | [A1570EA002B3](<Digital/AOC/AOC3296/A1570EA002B3>) |
| AOC              | AOC32B8 | L32WB81          | 1360x768  | 31.5 | 2009 | [B313130839D7](<Digital/AOC/AOC32B8/B313130839D7>) |
| AOC              | AOC3402 | U34G2G4R3        | 3440x1440 | 34.1 | 2024 | [10DB48ECA622](<Digital/AOC/AOC3402/10DB48ECA622>) |
| AOC              | AOC3402 | U34G2G4R3        | 3440x1440 | 34.1 | 2023 | [0C26087B9EE6](<Digital/AOC/AOC3402/0C26087B9EE6>) |
| AOC              | AOC3402 | U34G2G4R3        | 3440x1440 | 34.1 | 2022 | [0927AD396E21](<Digital/AOC/AOC3402/0927AD396E21>) |
| AOC              | AOC3402 | Q34E2G5          | 2560x1080 | 34.2 | 2022 | [21D817275FAE](<Digital/AOC/AOC3402/21D817275FAE>) |
| AOC              | AOC3402 | U34G2G1          | 3440x1440 | 34.1 | 2021 | [18F095D1E507](<Digital/AOC/AOC3402/18F095D1E507>) |
| AOC              | AOC3402 | U34G2G4R3        | 3440x1440 | 34.1 | 2020 | [01D87050C313](<Digital/AOC/AOC3402/01D87050C313>) |
| AOC              | AOC3402 | Q34E2G5          | 2560x1080 | 34.2 | 2020 | [29D229282C97](<Digital/AOC/AOC3402/29D229282C97>) |
| AOC              | AOC3402 | U34G2G4R3        | 3440x1440 | 34.1 | 2019 | [4F1463FF6E03](<Digital/AOC/AOC3402/4F1463FF6E03>) |
| AOC              | AOC3402 | U34G2G4R3        | 3440x1440 | 34.1 |      | [6A3CA10309FD](<Digital/AOC/AOC3402/6A3CA10309FD>) |
| AOC              | AOC3402 | Q34E2G5          | 2560x1080 | 34.2 |      | [B045FA8E3BA9](<Digital/AOC/AOC3402/B045FA8E3BA9>) |
| AOC              | AOC3403 | CU34P3C          | 3440x1440 | 34.1 | 2023 | [5B8C0FB988F1](<Digital/AOC/AOC3403/5B8C0FB988F1>) |
| AOC              | AOC3477 | Q3477            | 2560x1080 | 34.2 | 2016 | [FBBAA73FD2E9](<Digital/AOC/AOC3477/FBBAA73FD2E9>) |
| AOC              | AOC3477 | U3477            | 3440x1440 | 34.2 | 2015 | [EE67E79D9E9B](<Digital/AOC/AOC3477/EE67E79D9E9B>) |
| AOC              | AOC3477 | U3477            | 3440x1440 | 34.2 | 2014 | [5320C35C2C6D](<Digital/AOC/AOC3477/5320C35C2C6D>) |
| AOC              | AOC3520 | AG352QG2         | 2560x1080 | 35.1 | 2019 | [95CCE092FB85](<Digital/AOC/AOC3520/95CCE092FB85>) |
| AOC              | AOC3520 | AG352QG2         | 2560x1080 | 35.1 | 2017 | [1641A1911FD4](<Digital/AOC/AOC3520/1641A1911FD4>) |
| AOC              | AOC3520 | AG352QG2         | 2560x1080 | 35.1 | 2016 | [2F28D941086C](<Digital/AOC/AOC3520/2F28D941086C>) |
| AOC              | AOC3520 | AG352QG2         | 2560x1080 | 35.1 |      | [79FF669B719E](<Digital/AOC/AOC3520/79FF669B719E>) |
| AOC              | AOC3525 | AG352UCG6        | 3440x1440 | 35.1 | 2017 | [BDADE3DA112F](<Digital/AOC/AOC3525/BDADE3DA112F>) |
| AOC              | AOC3525 | AG352UCG         | 3440x1440 | 35.1 | 2016 | [3457AAC58EB8](<Digital/AOC/AOC3525/3457AAC58EB8>) |
| AOC              | AOC3525 | AG352UCG         | 3440x1440 | 35.1 |      | [051E0AB6DB83](<Digital/AOC/AOC3525/051E0AB6DB83>) |
| AOC              | AOC3583 | Q3583            | 2560x1080 | 35.1 | 2017 | [C5CCE7CF82B0](<Digital/AOC/AOC3583/C5CCE7CF82B0>) |
| AOC              | AOC3583 | Q3583            | 2560x1080 | 35.1 | 2015 | [244BF853F8A8](<Digital/AOC/AOC3583/244BF853F8A8>) |
| AOC              | AOC4008 | U4008B           | 3840x2160 | 40.2 | 2017 | [07EA0836D49B](<Digital/AOC/AOC4008/07EA0836D49B>) |
| AOC              | AOC4008 | 4008             | 1920x1080 | 40.2 | 2017 | [1171BDF38E9E](<Digital/AOC/AOC4008/1171BDF38E9E>) |
| AOC              | AOC4013 | LE40A1330/61     | 1920x1080 | 38.4 | 2012 | [5A8ED9F8184B](<Digital/AOC/AOC4013/5A8ED9F8184B>) |
| AOC              | AOC4220 | LE42D5520/20     | 1920x1080 | 42.5 | 2011 | [11410199976B](<Digital/AOC/AOC4220/11410199976B>) |
| AOC              | AOC4222 | LCD              | 1920x1080 | 41.9 | 2012 | [01D1CE04C544](<Digital/AOC/AOC4222/01D1CE04C544>) |
| AOC              | AOC4257 | LE42H057D        | 1920x1080 | 41.9 | 2010 | [DA49BD59D7CB](<Digital/AOC/AOC4257/DA49BD59D7CB>) |
| AOC              | AOC4298 | L42W98H          | 1360x768  | 28.9 | 2008 | [DD71B0A36EF3](<Digital/AOC/AOC4298/DD71B0A36EF3>) |
| AOC              | AOC4308 | U4308            | 3840x2160 | 42.5 | 2019 | [128EDE71C043](<Digital/AOC/AOC4308/128EDE71C043>) |
| AOC              | AOC4930 | AG493UG7R4       | 3840x1080 | 48.7 | 2022 | [054D974B037D](<Digital/AOC/AOC4930/054D974B037D>) |
| AOC              | AOC4930 | AG493UG7R4       | 3840x1080 | 48.7 | 2021 | [4895F8603662](<Digital/AOC/AOC4930/4895F8603662>) |
| AOC              | AOC4930 | AG493UG7R4       | 3840x1080 | 48.7 | 2020 | [09339E870770](<Digital/AOC/AOC4930/09339E870770>) |
| AOC              | AOC4930 | AG493UG7R4       | 3840x1080 | 48.7 | 2019 | [018F257E9A1C](<Digital/AOC/AOC4930/018F257E9A1C>) |
| AOC              | AOC4930 | AG493UG7R4       | 3840x1080 | 48.7 |      | [A0F13C802DB9](<Digital/AOC/AOC4930/A0F13C802DB9>) |
| AOC              | AOC9632 |                  | 1920x1080 | 23.1 | 2012 | [1EBF0171C25F](<Digital/AOC/AOC9632/1EBF0171C25F>) |
| AOC              | AOCA301 | AG493US3R4       | 3840x1080 | 48.7 | 2024 | [2B9ADB999279](<Digital/AOC/AOCA301/2B9ADB999279>) |
| AOC              | AOCA301 | AG493US3R4       | 3840x1080 | 48.7 | 2023 | [86919928BD81](<Digital/AOC/AOCA301/86919928BD81>) |
| AOC              | AOCA301 | AG493US3R4       | 3840x1080 | 48.7 | 2022 | [077926C706C5](<Digital/AOC/AOCA301/077926C706C5>) |
| AOC              | AOCA304 | AG493QS4R4       | 3840x1080 | 49.1 | 2024 | [8214B97A8DC1](<Digital/AOC/AOCA304/8214B97A8DC1>) |
| AOC              | AOCA304 | AG493QS4R4       | 3840x1080 | 49.1 | 2023 | [4277DA75EB29](<Digital/AOC/AOCA304/4277DA75EB29>) |
| AOC              | AOCA304 | AG493QS4R4       | 3840x1080 | 49.1 | 2021 | [2CDACB452A3A](<Digital/AOC/AOCA304/2CDACB452A3A>) |
| AOC              | AOCA409 | AG324UWS4R4B     | 3840x2160 | 31.5 | 2022 | [E4431FC8FA0E](<Digital/AOC/AOCA409/E4431FC8FA0E>) |
| AOC              | AOCA409 | AG324UWS4R4B     | 3840x2160 | 31.5 | 2020 | [7E096CCC2746](<Digital/AOC/AOCA409/7E096CCC2746>) |
| AOC              | AOCA412 | AG344UXM         | 3440x1440 | 34.2 | 2022 | [73230F92CE21](<Digital/AOC/AOCA412/73230F92CE21>) |
| AOC              | AOCA502 | AG275QG3R4B+     | 2560x1440 | 27.2 | 2022 | [226B14DF84A4](<Digital/AOC/AOCA502/226B14DF84A4>) |
| AOC              | AOCA503 | AG275QX          | 2560x1440 | 27.2 | 2023 | [19AFA839D5E8](<Digital/AOC/AOCA503/19AFA839D5E8>) |
| AOC              | AOCA504 | AG275QXN         | 2560x1440 | 27.2 | 2023 | [5E2580D9CB21](<Digital/AOC/AOCA504/5E2580D9CB21>) |
| AOC              | AOCA506 | AG275QZN         | 2560x1440 | 27.2 | 2024 | [3AF33DFBAE67](<Digital/AOC/AOCA506/3AF33DFBAE67>) |
| AOC              | AOCA506 | AG275QZN         | 2560x1440 | 27.2 | 2023 | [C82CBA18F44A](<Digital/AOC/AOCA506/C82CBA18F44A>) |
| AOC              | AOCA518 | AG405UXC         | 3440x1440 | 39.7 | 2024 | [2E8C2C6718B4](<Digital/AOC/AOCA518/2E8C2C6718B4>) |
| AOC              | AOCA518 | AG405UXC         | 3440x1440 | 39.7 | 2023 | [5639D5589D54](<Digital/AOC/AOCA518/5639D5589D54>) |
| AOC              | AOCA522 | LM522            | 1024x768  | 14.9 | 2008 | [832CC548293F](<Digital/AOC/AOCA522/832CC548293F>) |
| AOC              | AOCA524 | AG275UXM         | 3840x2160 | 27.2 | 2024 | [C28C108336FB](<Digital/AOC/AOCA524/C28C108336FB>) |
| AOC              | AOCA562 | LM520/LM520A     | 1024x768  | 14.9 |      | [CA79C416E263](<Digital/AOC/AOCA562/CA79C416E263>) |
| AOC              | AOCA601 | AG276QZD         | 2560x1440 | 26.6 | 2024 | [7621A3026A80](<Digital/AOC/AOCA601/7621A3026A80>) |
| AOC              | AOCA601 | AG276QZD         | 2560x1440 | 26.6 | 2023 | [0233F676A047](<Digital/AOC/AOCA601/0233F676A047>) |
| AOC              | AOCA610 | AG276QZD2        | 2560x1440 | 26.6 | 2024 | [23970B4B5A93](<Digital/AOC/AOCA610/23970B4B5A93>) |
| AOC              | AOCA611 | AG326UD          | 3840x2160 | 31.7 | 2025 | [ED40064E00FE](<Digital/AOC/AOCA611/ED40064E00FE>) |
| AOC              | AOCA611 | AG326UD          | 3840x2160 | 31.7 | 2024 | [3EE44715D64D](<Digital/AOC/AOCA611/3EE44715D64D>) |
| AOC              | AOCA781 | LM720/LM720A     | 1280x1024 | 17.1 | 2003 | [C2564233342B](<Digital/AOC/AOCA781/C2564233342B>) |
| AOC              | AOCA784 | LM729            | 1280x1024 | 17.1 | 2006 | [F08FBBA404C1](<Digital/AOC/AOCA784/F08FBBA404C1>) |
| AOC              | AOCA784 | LM729            | 1280x1024 | 17.1 | 2003 | [3E37098FFF4E](<Digital/AOC/AOCA784/3E37098FFF4E>) |
| AOC              | AOCA784 | LM729            | 1280x1024 | 17.1 |      | [43DCED17508B](<Digital/AOC/AOCA784/43DCED17508B>) |
| AOC              | AOCA786 | LM765            | 1280x1024 | 17.1 | 2006 | [511C5A34A2D8](<Digital/AOC/AOCA786/511C5A34A2D8>) |
| AOC              | AOCA925 | LM925            | 1280x1024 | 19.1 |      | [BC08C3C7C609](<Digital/AOC/AOCA925/BC08C3C7C609>) |
| AOC              | AOCA981 | LM914/LM919      | 1280x1024 | 19.1 |      | [0D5717FA37FD](<Digital/AOC/AOCA981/0D5717FA37FD>) |
| AOC              | AOCA985 | LM960            | 1280x1024 | 19.1 | 2006 | [71AF38ECE150](<Digital/AOC/AOCA985/71AF38ECE150>) |
| AOC              | AOCA991 | 9K+              | 1600x1200 | 17.7 | 2004 | [404B7C1C34D3](<Digital/AOC/AOCA991/404B7C1C34D3>) |
| AOC              | AOCB201 | U28G2G4R4        | 3840x2160 | 27.8 | 2022 | [16698B2168A8](<Digital/AOC/AOCB201/16698B2168A8>) |
| AOC              | AOCB201 | U28G2G4R4        | 3840x2160 | 27.8 | 2021 | [5D40928605B8](<Digital/AOC/AOCB201/5D40928605B8>) |
| AOC              | AOCB203 | 24G2W1G8         | 1920x1080 | 24.0 | 2024 | [02FC96031318](<Digital/AOC/AOCB203/02FC96031318>) |
| AOC              | AOCB203 | 24G2W1G8         | 1920x1080 | 24.0 | 2023 | [1B5F79C2B698](<Digital/AOC/AOCB203/1B5F79C2B698>) |
| AOC              | AOCB203 | 24G2W1G8         | 1920x1080 | 24.0 | 2022 | [63DF00FE6910](<Digital/AOC/AOCB203/63DF00FE6910>) |
| AOC              | AOCB205 | Q24G2            | 2560x1440 | 24.0 | 2025 | [F93B7341176E](<Digital/AOC/AOCB205/F93B7341176E>) |
| AOC              | AOCB205 | Q24G2            | 2560x1440 | 24.0 | 2024 | [2C996237DAA6](<Digital/AOC/AOCB205/2C996237DAA6>) |
| AOC              | AOCB205 | Q24G2            | 2560x1440 | 24.0 | 2023 | [0EA081B3F3A0](<Digital/AOC/AOCB205/0EA081B3F3A0>) |
| AOC              | AOCB206 | CU34G2XP         | 3440x1440 | 34.1 | 2025 | [1B1D9B6DAEE6](<Digital/AOC/AOCB206/1B1D9B6DAEE6>) |
| AOC              | AOCB206 | CU34G2XP         | 3440x1440 | 34.1 | 2024 | [27BF57543093](<Digital/AOC/AOCB206/27BF57543093>) |
| AOC              | AOCB206 | CU34G2XP         | 3440x1440 | 34.1 | 2023 | [874611012FB1](<Digital/AOC/AOCB206/874611012FB1>) |
| AOC              | AOCB207 | 24G2E1           | 1920x1080 | 24.0 | 2025 | [76A90CA20912](<Digital/AOC/AOCB207/76A90CA20912>) |
| AOC              | AOCB207 | 24G2E1           | 1920x1080 | 24.0 | 2024 | [1504E8EDA7C3](<Digital/AOC/AOCB207/1504E8EDA7C3>) |
| AOC              | AOCB208 | 27G2E1           | 1920x1080 | 27.2 | 2024 | [05AFD75CB796](<Digital/AOC/AOCB208/05AFD75CB796>) |
| AOC              | AOCB210 | CQ27G2S          | 2560x1440 | 27.2 | 2024 | [290652B7674A](<Digital/AOC/AOCB210/290652B7674A>) |
| AOC              | AOCB210 | CQ27G2S          | 2560x1440 | 27.2 | 2023 | [5AE15A44FC29](<Digital/AOC/AOCB210/5AE15A44FC29>) |
| AOC              | AOCB211 | CU34G2XE         | 3440x1440 | 34.1 | 2024 | [06062CF7FCEE](<Digital/AOC/AOCB211/06062CF7FCEE>) |
| AOC              | AOCB211 | CU34G2XE         | 3440x1440 | 34.1 | 2023 | [348470C5FA4D](<Digital/AOC/AOCB211/348470C5FA4D>) |
| AOC              | AOCB304 | 32G3WG3-         | 1920x1080 | 31.5 | 2021 | [A6EF315C3892](<Digital/AOC/AOCB304/A6EF315C3892>) |
| AOC              | AOCB305 | Q32G3WG3R3       | 2560x1440 | 31.5 | 2024 | [051040BCDA55](<Digital/AOC/AOCB305/051040BCDA55>) |
| AOC              | AOCB305 | Q32G3WG3R3       | 2560x1440 | 31.5 | 2023 | [3264E1105B69](<Digital/AOC/AOCB305/3264E1105B69>) |
| AOC              | AOCB305 | Q32G3WG3R3       | 2560x1440 | 31.5 | 2022 | [0BB865289C35](<Digital/AOC/AOCB305/0BB865289C35>) |
| AOC              | AOCB305 | Q32G3WG3R3       | 2560x1440 | 31.5 | 2021 | [2E8D77D5AC6E](<Digital/AOC/AOCB305/2E8D77D5AC6E>) |
| AOC              | AOCB306 | U34G3G3R3        | 3440x1440 | 34.1 | 2023 | [1CF3A7B6BB13](<Digital/AOC/AOCB306/1CF3A7B6BB13>) |
| AOC              | AOCB306 | U34G3G3R3        | 3440x1440 | 34.1 | 2022 | [24F26463273E](<Digital/AOC/AOCB306/24F26463273E>) |
| AOC              | AOCB306 | U34G3G3R3        | 3440x1440 | 34.1 | 2021 | [927E028F10DD](<Digital/AOC/AOCB306/927E028F10DD>) |
| AOC              | AOCB309 | Q27G3G3R3        | 2560x1440 | 27.2 | 2022 | [F26EACDA8AC3](<Digital/AOC/AOCB309/F26EACDA8AC3>) |
| AOC              | AOCB309 | Q27G3G3R3        | 2560x1440 | 27.2 | 2021 | [3574346B01A1](<Digital/AOC/AOCB309/3574346B01A1>) |
| AOC              | AOCB314 | Q27G3WG8         | 2560x1440 | 27.2 | 2024 | [17C94DF3FCD6](<Digital/AOC/AOCB314/17C94DF3FCD6>) |
| AOC              | AOCB316 | U34G3XM          | 3440x1440 | 34.1 | 2023 | [0D02BF842870](<Digital/AOC/AOCB316/0D02BF842870>) |
| AOC              | AOCB316 | U34G3XM          | 3440x1440 | 34.1 | 2022 | [109FDD80CF5F](<Digital/AOC/AOCB316/109FDD80CF5F>) |
| AOC              | AOCB319 | U32G3X           | 3840x2160 | 31.5 | 2023 | [9D943F4A751E](<Digital/AOC/AOCB319/9D943F4A751E>) |
| AOC              | AOCB320 | U27G3X           | 3840x2160 | 27.2 | 2024 | [1657CE532721](<Digital/AOC/AOCB320/1657CE532721>) |
| AOC              | AOCB320 | U27G3X           | 3840x2160 | 27.2 | 2023 | [567FAE57E65B](<Digital/AOC/AOCB320/567FAE57E65B>) |
| AOC              | AOCB321 | Q27G3Z           | 2560x1440 | 27.2 | 2023 | [D52CD81BAC4E](<Digital/AOC/AOCB321/D52CD81BAC4E>) |
| AOC              | AOCB322 | 25G3ZM           | 1920x1080 | 24.3 | 2024 | [81FEFF3C6617](<Digital/AOC/AOCB322/81FEFF3C6617>) |
| AOC              | AOCB322 | 25G3ZM           | 1920x1080 | 24.3 | 2023 | [8017BD47955C](<Digital/AOC/AOCB322/8017BD47955C>) |
| AOC              | AOCB322 | 25G3ZM           | 1920x1080 | 24.3 | 2022 | [4E3BC5FA8517](<Digital/AOC/AOCB322/4E3BC5FA8517>) |
| AOC              | AOCB326 | Q27G3XMN         | 2560x1440 | 27.2 | 2025 | [0CE33840A56B](<Digital/AOC/AOCB326/0CE33840A56B>) |
| AOC              | AOCB326 | Q27G3XMN         | 2560x1440 | 27.2 | 2024 | [03D4C41CCFA4](<Digital/AOC/AOCB326/03D4C41CCFA4>) |
| AOC              | AOCB326 | Q27G3XMN         | 2560x1440 | 27.2 | 2023 | [1B665CEEEEFB](<Digital/AOC/AOCB326/1B665CEEEEFB>) |
| AOC              | AOCB401 | 24G4             | 1920x1080 | 24.0 | 2025 | [6FD6FAF4C90D](<Digital/AOC/AOCB401/6FD6FAF4C90D>) |
| AOC              | AOCB401 | 24G4             | 1920x1080 | 24.0 | 2024 | [0FAAEE2990DA](<Digital/AOC/AOCB401/0FAAEE2990DA>) |
| AOC              | AOCB401 | 24G4             | 1920x1080 | 24.0 | 2023 | [09FDAEC3D642](<Digital/AOC/AOCB401/09FDAEC3D642>) |
| AOC              | AOCB402 | 27G4             | 1920x1080 | 27.2 | 2025 | [2A897CA28B45](<Digital/AOC/AOCB402/2A897CA28B45>) |
| AOC              | AOCB402 | 27G4             | 1920x1080 | 27.2 | 2024 | [150B055DA618](<Digital/AOC/AOCB402/150B055DA618>) |
| AOC              | AOCB402 | 27G4             | 1920x1080 | 27.2 | 2023 | [28E184849A59](<Digital/AOC/AOCB402/28E184849A59>) |
| AOC              | AOCB403 | Q27G4            | 2560x1440 | 27.2 | 2025 | [19FD019D9863](<Digital/AOC/AOCB403/19FD019D9863>) |
| AOC              | AOCB403 | Q27G4            | 2560x1440 | 27.2 | 2024 | [099E05C75D88](<Digital/AOC/AOCB403/099E05C75D88>) |
| AOC              | AOCB403 | Q27G4            | 2560x1440 | 27.2 | 2023 | [C492F7DEBD14](<Digital/AOC/AOCB403/C492F7DEBD14>) |
| AOC              | AOCB404 | Q27G4N           | 2560x1440 | 27.2 | 2024 | [03E933810C73](<Digital/AOC/AOCB404/03E933810C73>) |
| AOC              | AOCB404 | Q27G4N           | 2560x1440 | 27.2 | 2023 | [62C00BED51DD](<Digital/AOC/AOCB404/62C00BED51DD>) |
| AOC              | AOCB405 | C27G4Z           | 1920x1080 | 27.2 | 2024 | [38276DC21443](<Digital/AOC/AOCB405/38276DC21443>) |
| AOC              | AOCB407 | CQ27G4           | 2560x1440 | 27.2 | 2025 | [46D5A63E83E4](<Digital/AOC/AOCB407/46D5A63E83E4>) |
| AOC              | AOCB407 | CQ27G4           | 2560x1440 | 27.2 | 2024 | [8B8B96FCF3F2](<Digital/AOC/AOCB407/8B8B96FCF3F2>) |
| AOC              | AOCB408 | CQ32G4           | 2560x1440 | 31.5 | 2024 | [32FF555CE961](<Digital/AOC/AOCB408/32FF555CE961>) |
| AOC              | AOCB409 | C27G4            | 1920x1080 | 27.2 | 2024 | [12659EF26D81](<Digital/AOC/AOCB409/12659EF26D81>) |
| AOC              | AOCB410 | Q24G4            | 2560x1440 | 24.0 | 2025 | [133D7F640532](<Digital/AOC/AOCB410/133D7F640532>) |
| AOC              | AOCB415 | 24G42E           | 1920x1080 | 24.0 | 2025 | [2EF09A3489FA](<Digital/AOC/AOCB415/2EF09A3489FA>) |
| AOC              | AOCB419 | CU34G4           | 3440x1440 | 34.1 | 2025 | [4C91352EBE07](<Digital/AOC/AOCB419/4C91352EBE07>) |
| AOC              | AOCB421 | Q27G4ZD          | 2560x1440 | 26.6 | 2025 | [74050BCDD056](<Digital/AOC/AOCB421/74050BCDD056>) |
| AOC              | AOCB423 | Q25G4S           | 2560x1440 | 24.3 | 2025 | [E3C74E6756DF](<Digital/AOC/AOCB423/E3C74E6756DF>) |
| AOC              | AOCB431 | 27G42E           | 1920x1080 | 27.2 | 2025 | [879BE3492678](<Digital/AOC/AOCB431/879BE3492678>) |
| AOC              | AOCB437 | Q27G42XE         | 2560x1440 | 27.2 | 2025 | [4F3024D40D94](<Digital/AOC/AOCB437/4F3024D40D94>) |
| AOC              | AOCB440 | 27G4H            | 1920x1080 | 27.2 | 2025 | [7FD433CBBABB](<Digital/AOC/AOCB440/7FD433CBBABB>) |
| AOC              | AOCB458 | Q27G42ZE         | 2560x1440 | 27.2 | 2025 | [1B349991ED1D](<Digital/AOC/AOCB458/1B349991ED1D>) |
| AOC              | AOCB467 | 27G4HRE          | 1920x1080 | 27.2 | 2025 | [B356B8BC2A12](<Digital/AOC/AOCB467/B356B8BC2A12>) |
| AOC              | AOCB469 | U34G4C           | 3440x1440 | 34.1 | 2025 | [EA919D99A23E](<Digital/AOC/AOCB469/EA919D99A23E>) |
| AOC              | AOCB473 | U27G4R           | 3840x2160 | 27.2 | 2025 | [A11770E6239B](<Digital/AOC/AOCB473/A11770E6239B>) |
| AOC              | AOCB905 | G4309VX_D        | 3840x2160 | 42.5 | 2023 | [9E3D939DEE8C](<Digital/AOC/AOCB905/9E3D939DEE8C>) |
| AOC              | AOCBA02 | 24G30E           | 1920x1080 | 24.0 | 2024 | [07EAF88D25D4](<Digital/AOC/AOCBA02/07EAF88D25D4>) |
| AOC              | AOCC745 | LM745s           | 1280x1024 | 17.1 | 2006 | [08C8F57AE36C](<Digital/AOC/AOCC745/08C8F57AE36C>) |
| AOC              | AOCC942 | LM942            | 1280x1024 | 19.1 | 2007 | [7CA6973DC1DE](<Digital/AOC/AOCC942/7CA6973DC1DE>) |
| AOC              | AOCC981 | WJ1980PI-2       | 1280x1024 | 19.1 | 2006 | [AF290FD285FA](<Digital/AOC/AOCC981/AF290FD285FA>) |
| AOC              | AOCD201 | PD32M            | 3840x2160 | 31.5 | 2023 | [C4165A714BCF](<Digital/AOC/AOCD201/C4165A714BCF>) |
| AOC              | AOCD203 | PD27S            | 2560x1440 | 27.2 | 2022 | [40D9883D744D](<Digital/AOC/AOCD203/40D9883D744D>) |
| AOC              | AOCE505 | 24V5CE           | 1920x1080 | 24.0 | 2022 | [BD03249AB8B1](<Digital/AOC/AOCE505/BD03249AB8B1>) |
| AOC              | AOCE508 | 27V5C            | 1920x1080 | 27.2 | 2022 | [1582BD004F39](<Digital/AOC/AOCE508/1582BD004F39>) |
| AOC              | AOCE509 | Q27V5C           | 2560x1440 | 27.2 | 2022 | [58D39530EC6C](<Digital/AOC/AOCE509/58D39530EC6C>) |
| AOC              | AOCE510 | Q32V5CE          | 2560x1440 | 31.5 | 2023 | [0F01C7823448](<Digital/AOC/AOCE510/0F01C7823448>) |
| AOC              | AOCE510 | Q32V5CE          | 2560x1440 | 31.5 | 2022 | [529F7FC0DD61](<Digital/AOC/AOCE510/529F7FC0DD61>) |
| AOC              | AOCE511 | CU34V5C          | 3440x1440 | 34.1 | 2024 | [6605B5CF4C14](<Digital/AOC/AOCE511/6605B5CF4C14>) |
| AOC              | AOCE511 | CU34V5C          | 3440x1440 | 34.1 | 2023 | [2D5932B90303](<Digital/AOC/AOCE511/2D5932B90303>) |
| AOC              | AOCE513 | Q27V5CW          | 2560x1440 | 27.2 | 2022 | [7319184602AB](<Digital/AOC/AOCE513/7319184602AB>) |
| AOC              | AOCE515 | Q27V5N           | 2560x1440 | 27.2 | 2023 | [C075688DA0F1](<Digital/AOC/AOCE515/C075688DA0F1>) |
| AOC              | AOCE516 | U34V5C           | 3440x1440 | 34.1 | 2023 | [FC61357826A4](<Digital/AOC/AOCE516/FC61357826A4>) |
| AOC              | AOCE556 | CT500G           | 1024x768  | 13.8 | 2006 | [7B7157442E28](<Digital/AOC/AOCE556/7B7157442E28>) |
| AOpen            | AOP0000 | 27HC5R           | 1920x1080 | 27.2 | 2020 | [22424C2642E2](<Digital/AOpen/AOP0000/22424C2642E2>) |
| AOpen            | AOP069C | 24HC1QR          | 1920x1080 | 23.6 | 2020 | [157F5B13E3F9](<Digital/AOpen/AOP069C/157F5B13E3F9>) |
| AOpen            | AOP069E | 32HC1QUR P       | 2560x1440 | 31.5 | 2018 | [2BCCF2C0E3FC](<Digital/AOpen/AOP069E/2BCCF2C0E3FC>) |
| AOpen            | AOP06A4 | 22MX1Q           | 1920x1080 | 21.7 | 2019 | [401AB8D58806](<Digital/AOpen/AOP06A4/401AB8D58806>) |
| AOpen            | AOP06A5 | 20CH1Q           | 1366x768  | 19.4 | 2022 | [D150F1790D88](<Digital/AOpen/AOP06A5/D150F1790D88>) |
| AOpen            | AOP06A5 | 20CH1Q           | 1366x768  | 19.4 | 2020 | [719E48D54735](<Digital/AOpen/AOP06A5/719E48D54735>) |
| AOpen            | AOP06A5 | 20CH1Q           | 1366x768  | 19.4 | 2019 | [DDFC8ADEF1B5](<Digital/AOpen/AOP06A5/DDFC8ADEF1B5>) |
| AOpen            | AOP06AA | 27ML2            | 1920x1080 | 27.2 | 2020 | [755F55CBEC44](<Digital/AOpen/AOP06AA/755F55CBEC44>) |
| AOpen            | AOP06B3 | 27MX1            | 1920x1080 | 27.2 | 2019 | [2E0F272A4A99](<Digital/AOpen/AOP06B3/2E0F272A4A99>) |
| AOpen            | AOP06B4 | 24MX1            | 1920x1080 | 24.0 | 2020 | [1B0BCDE57686](<Digital/AOpen/AOP06B4/1B0BCDE57686>) |
| AOpen            | AOP06B5 | 24ML1Y           | 1920x1080 | 24.0 | 2020 | [D547D127680D](<Digital/AOpen/AOP06B5/D547D127680D>) |
| AOpen            | AOP06C3 | 22CH1Q           | 1920x1080 | 21.7 | 2019 | [559F5EA6EF3E](<Digital/AOpen/AOP06C3/559F5EA6EF3E>) |
| AOpen            | AOP06C8 | 27ML1U           | 2560x1440 | 27.2 | 2019 | [304605A7E89E](<Digital/AOpen/AOP06C8/304605A7E89E>) |
| AOpen            | AOP06C8 | 27ML1U           | 2560x1440 | 27.2 | 2018 | [EF7305B6F2BC](<Digital/AOpen/AOP06C8/EF7305B6F2BC>) |
| AOpen            | AOP0712 | 24CH3Y           | 1920x1080 | 24.0 | 2022 | [1BC2446D0D3C](<Digital/AOpen/AOP0712/1BC2446D0D3C>) |
| AOpen            | AOP0757 | 22CV1Q           | 1920x1080 | 21.7 | 2020 | [38F78C85722C](<Digital/AOpen/AOP0757/38F78C85722C>) |
| AOpen            | AOP0758 | 24CL1Y           | 1920x1080 | 24.0 | 2020 | [158A4E0DB1A8](<Digital/AOpen/AOP0758/158A4E0DB1A8>) |
| AOpen            | AOP077C | 24CH2Y           | 1920x1080 | 24.0 | 2020 | [8666C60B41C5](<Digital/AOpen/AOP077C/8666C60B41C5>) |
| AOpen            | AOP077C | 24CH2Y           | 1920x1080 | 24.0 |      | [2528FACB37F6](<Digital/AOpen/AOP077C/2528FACB37F6>) |
| AOpen            | AOP0806 | 22CV1Q           | 1920x1080 | 21.5 | 2022 | [1117EA3658F3](<Digital/AOpen/AOP0806/1117EA3658F3>) |
| AOpen            | AOP0806 | 22CV1Q           | 1920x1080 | 21.5 | 2021 | [47E5EAC4FD2F](<Digital/AOpen/AOP0806/47E5EAC4FD2F>) |
| AOpen            | AOP0807 | 24CL1Y           | 1920x1080 | 24.0 | 2021 | [058E4F5268BF](<Digital/AOpen/AOP0807/058E4F5268BF>) |
| AOpen            | AOP0808 | 27HC5R           | 1920x1080 | 27.2 | 2022 | [71E5BBB10E2D](<Digital/AOpen/AOP0808/71E5BBB10E2D>) |
| AOpen            | AOP0808 | 27HC5R P         | 1920x1080 | 27.0 | 2021 | [CCEC78EA4526](<Digital/AOpen/AOP0808/CCEC78EA4526>) |
| AOpen            | AOP0809 | 32HC5QR P        | 1920x1080 | 31.5 | 2022 | [01E2F5F97420](<Digital/AOpen/AOP0809/01E2F5F97420>) |
| AOpen            | AOP080C | 27HC5R X/Z       | 1920x1080 | 27.0 | 2021 | [79B4E384018B](<Digital/AOpen/AOP080C/79B4E384018B>) |
| AOpen            | AOP0810 | 27HC5UR P/S      | 2560x1440 | 27.0 | 2021 | [A0063C8D0D76](<Digital/AOpen/AOP0810/A0063C8D0D76>) |
| AOpen            | AOP08E5 | 27HC5R           | 1920x1080 | 27.0 | 2022 | [128581EFA2AB](<Digital/AOpen/AOP08E5/128581EFA2AB>) |
| AOpen            | AOP08E6 | 27HC5UR          | 2560x1440 | 27.2 | 2021 | [7101AF8F87B9](<Digital/AOpen/AOP08E6/7101AF8F87B9>) |
| AOpen            | AOP0910 | 16PM6Q           | 1920x1080 | 15.7 | 2022 | [1E26C812B907](<Digital/AOpen/AOP0910/1E26C812B907>) |
| AOpen            | AOP0910 | 16PM6Q           | 1920x1080 | 15.7 | 2021 | [097F1969C9F7](<Digital/AOpen/AOP0910/097F1969C9F7>) |
| AOpen            | AOP0912 | 24MV1Y P         | 1920x1080 | 24.2 | 2021 | [2CD85367ACB1](<Digital/AOpen/AOP0912/2CD85367ACB1>) |
| AOpen            | AOP091C | 27HC5R V         | 1920x1080 | 27.0 | 2023 | [329E581ACF0B](<Digital/AOpen/AOP091C/329E581ACF0B>) |
| AOpen            | AOP091F | 34HC5CUR P       | 3440x1440 | 34.1 | 2023 | [1EF6DACBE8B2](<Digital/AOpen/AOP091F/1EF6DACBE8B2>) |
| AOpen            | AOP091F | 34HC5CUR P       | 3440x1440 | 34.1 | 2022 | [1984D0A7201D](<Digital/AOpen/AOP091F/1984D0A7201D>) |
| AOpen            | AOP0948 | 24CV1Y           | 1920x1080 | 24.0 | 2022 | [3B3EB3E42461](<Digital/AOpen/AOP0948/3B3EB3E42461>) |
| AOpen            | AOP0A87 | 27SA2            | 1920x1080 | 27.0 | 2022 | [4294A7C414E3](<Digital/AOpen/AOP0A87/4294A7C414E3>) |
| AOpen            | AOP0B0B | 24SA2Y           | 1920x1080 | 23.8 | 2023 | [355CBF229F5B](<Digital/AOpen/AOP0B0B/355CBF229F5B>) |
| AOpen            | AOP0B0B | 24SA2Y           | 1920x1080 | 23.8 | 2022 | [D1A347899697](<Digital/AOpen/AOP0B0B/D1A347899697>) |
| AOpen            | AOP0B0C | 27SA2 E          | 1920x1080 | 27.2 | 2024 | [146789F148A5](<Digital/AOpen/AOP0B0C/146789F148A5>) |
| AOpen            | AOP0B0C | 27SA2            | 1920x1080 | 27.0 | 2023 | [74D76D97FB2D](<Digital/AOpen/AOP0B0C/74D76D97FB2D>) |
| AOpen            | AOP0B95 | 22CV1Q H3        | 1920x1080 | 21.5 | 2025 | [13AE17D98D87](<Digital/AOpen/AOP0B95/13AE17D98D87>) |
| AOpen            | AOP0B95 | 22CV1Q H3        | 1920x1080 | 21.5 | 2023 | [352329509CA9](<Digital/AOpen/AOP0B95/352329509CA9>) |
| AOpen            | AOP0B9B | 20E0Q            | 1600x900  | 19.5 | 2024 | [F0AD27DA5A6F](<Digital/AOpen/AOP0B9B/F0AD27DA5A6F>) |
| AOpen            | AOP0C0D | 24CL1Y E         | 1920x1080 | 23.8 | 2025 | [2C1D90532B0B](<Digital/AOpen/AOP0C0D/2C1D90532B0B>) |
| AOpen            | AOP0C0D | 24CL1Y E         | 1920x1080 | 23.8 | 2024 | [9F6DC93D00B3](<Digital/AOpen/AOP0C0D/9F6DC93D00B3>) |
| AOpen            | AOP0C0D | 24CL1Y E         | 1920x1080 | 23.8 | 2023 | [40930584BBCF](<Digital/AOpen/AOP0C0D/40930584BBCF>) |
| AOpen            | AOP0C0F | 27CL1 E          | 1920x1080 | 27.0 | 2024 | [2B8CFA8BB6B2](<Digital/AOpen/AOP0C0F/2B8CFA8BB6B2>) |
| AOpen            | AOP0C39 | 27SH2            | 1920x1080 | 27.0 | 2023 | [2BA5DA058A5E](<Digital/AOpen/AOP0C39/2BA5DA058A5E>) |
| AOpen            | AOP0CA4 | 27HC5UR P2       | 2560x1440 | 27.0 | 2023 | [239913893D18](<Digital/AOpen/AOP0CA4/239913893D18>) |
| AOpen            | AOP0CA9 | 24KG3Y M3        | 1920x1080 | 24.0 | 2024 | [F60161418FEC](<Digital/AOpen/AOP0CA9/F60161418FEC>) |
| AOpen            | AOP0CA9 | 24KG3Y M3        | 1920x1080 | 23.8 | 2023 | [87EC36423850](<Digital/AOpen/AOP0CA9/87EC36423850>) |
| AOpen            | AOP0CAA | 27KG3 M3         | 1920x1080 | 27.0 | 2024 | [91647F5C51D1](<Digital/AOpen/AOP0CAA/91647F5C51D1>) |
| AOpen            | AOP0CF2 | 16PM1QB          | 1920x1080 | 15.6 | 2024 | [27B2162715D6](<Digital/AOpen/AOP0CF2/27B2162715D6>) |
| AOpen            | AOP0CFD | 32SA2QK          | 3840x2160 | 31.5 | 2024 | [8D0B46532A48](<Digital/AOpen/AOP0CFD/8D0B46532A48>) |
| AOpen            | AOP0D41 | 22CL1Q E3        | 1920x1080 | 21.5 | 2025 | [0E335D9BED12](<Digital/AOpen/AOP0D41/0E335D9BED12>) |
| AOpen            | AOP0D92 | 34HC5CU S3       | 3440x1440 | 34.0 | 2024 | [D8FB370017CE](<Digital/AOpen/AOP0D92/D8FB370017CE>) |
| AOpen            | AOP0EAC | 16PM1Q J         | 1920x1080 | 15.7 | 2025 | [80C6E008EB38](<Digital/AOpen/AOP0EAC/80C6E008EB38>) |
| AOpen            | AOP0EBC | 24CL1Y G0        | 1920x1080 | 23.8 | 2024 | [8F51EDC7E766](<Digital/AOpen/AOP0EBC/8F51EDC7E766>) |
| AOpen            | AOP0F21 | 27CL1 G          | 1920x1080 | 27.0 | 2024 | [9A4AA987B12E](<Digital/AOpen/AOP0F21/9A4AA987B12E>) |
| AOpen            | AOP2136 | RTD2136R-FHD     | 1920x1080 | 21.7 | 2010 | [32D1AB0F97E1](<Digital/AOpen/AOP2136/32D1AB0F97E1>) |
| ASRock           | ASRAAA0 | PG32QF2B         | 2560x1440 | 31.5 | 2024 | [14FE62C520F9](<Digital/ASRock/ASRAAA0/14FE62C520F9>) |
| ASRock           | ASRAAA0 | PG32QF2B         | 2560x1440 | 31.5 | 2023 | [650859575A89](<Digital/ASRock/ASRAAA0/650859575A89>) |
| ASRock           | ASRAAA1 | PG34WQ15R3A      | 3440x1440 | 34.1 | 2022 | [F2198FE75848](<Digital/ASRock/ASRAAA1/F2198FE75848>) |
| ASRock           | ASRABA0 | PG27FF1A         | 1920x1080 | 27.2 | 2024 | [C993B7EC7425](<Digital/ASRock/ASRABA0/C993B7EC7425>) |
| ASRock           | ASRABA0 | PG27FF1A         | 1920x1080 | 27.2 | 2023 | [450FB82FBC84](<Digital/ASRock/ASRABA0/450FB82FBC84>) |
| ASRock           | ASRABA0 | PG27FF1A         | 1920x1080 | 27.2 | 2022 | [2CD07B87B267](<Digital/ASRock/ASRABA0/2CD07B87B267>) |
| ASRock           | ASRABA1 | PG27QFT1B        | 2560x1440 | 27.2 | 2024 | [0EF966B921E8](<Digital/ASRock/ASRABA1/0EF966B921E8>) |
| ASRock           | ASRABA2 | PG27QFT2A        | 2560x1440 | 27.2 | 2024 | [4D768B54B0FC](<Digital/ASRock/ASRABA2/4D768B54B0FC>) |
| ASRock           | ASRABA4 | PG27FFT1B        | 1920x1080 | 27.2 | 2024 | [B3864B7C7555](<Digital/ASRock/ASRABA4/B3864B7C7555>) |
| ASRock           | ASRABA5 | PG27FFX1B        | 1920x1080 | 27.2 | 2024 | [848CC32B72DD](<Digital/ASRock/ASRABA5/848CC32B72DD>) |
| ASRock           | ASRACA1 | PG27Q15R2A       | 2560x1440 | 27.2 | 2023 | [63807ABB6D58](<Digital/ASRock/ASRACA1/63807ABB6D58>) |
| ASRock           | ASRACA3 | PG27F15RS1A      | 1920x1080 | 27.2 | 2023 | [355183B190FC](<Digital/ASRock/ASRACA3/355183B190FC>) |
| ASRock           | ASRACA7 | PG25FFT          | 1920x1080 | 24.5 | 2024 | [7E618F8FD49D](<Digital/ASRock/ASRACA7/7E618F8FD49D>) |
| ASRock           | ASRBCA0 | CL25FF           | 1920x1080 | 24.5 | 2023 | [7502C9855922](<Digital/ASRock/ASRBCA0/7502C9855922>) |
| ASRock           | ASRBCA2 | CL25FFA          | 1920x1080 | 24.5 | 2024 | [BD9E4230C284](<Digital/ASRock/ASRBCA2/BD9E4230C284>) |
| ASUS             | ASU238C | V241DA           | 1920x1080 | 24.2 | 2020 | [0D14CF6324D6](<Digital/ASUS/ASU238C/0D14CF6324D6>) |
| ASUS             | ASU282C | V241FA           | 1920x1080 | 24.2 | 2017 | [0C4E38AF589B](<Digital/ASUS/ASU282C/0C4E38AF589B>) |
| ASUS             | AUS0003 | S2               | 1920x1080 | 36.1 | 2018 | [6CE1E78E4FD9](<Digital/ASUS/AUS0003/6CE1E78E4FD9>) |
| ASUS             | AUS1461 | PA148            | 1920x1080 | 13.9 | 2023 | [BF60A2FC7258](<Digital/ASUS/AUS1461/BF60A2FC7258>) |
| ASUS             | AUS1461 | PA148            | 1920x1080 | 13.9 | 2021 | [3F4087AB6D46](<Digital/ASUS/AUS1461/3F4087AB6D46>) |
| ASUS             | AUS14B1 | MB14AC           | 1920x1080 | 13.9 | 2023 | [8452C58502B0](<Digital/ASUS/AUS14B1/8452C58502B0>) |
| ASUS             | AUS14B1 | MB14AC           | 1920x1080 | 13.9 | 2022 | [1133C1796E8B](<Digital/ASUS/AUS14B1/1133C1796E8B>) |
| ASUS             | AUS14B1 | MB14AC           | 1920x1080 | 13.9 | 2020 | [4A154F28FA9E](<Digital/ASUS/AUS14B1/4A154F28FA9E>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2024 | [3485A539F010](<Digital/ASUS/AUS1641/3485A539F010>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2023 | [0883C877FF93](<Digital/ASUS/AUS1641/0883C877FF93>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2022 | [270C80962CB8](<Digital/ASUS/AUS1641/270C80962CB8>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2021 | [67E7B35EEC75](<Digital/ASUS/AUS1641/67E7B35EEC75>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2020 | [09F2398EFBA0](<Digital/ASUS/AUS1641/09F2398EFBA0>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2019 | [0D8F64B70EDF](<Digital/ASUS/AUS1641/0D8F64B70EDF>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2018 | [7E06B6371DA4](<Digital/ASUS/AUS1641/7E06B6371DA4>) |
| ASUS             | AUS1641 | MB16AC           | 1920x1080 | 15.3 | 2017 | [328B13E19C86](<Digital/ASUS/AUS1641/328B13E19C86>) |
| ASUS             | AUS1641 |                  | 1920x1080 | 15.3 |      | [F5A54F2C0E39](<Digital/ASUS/AUS1641/F5A54F2C0E39>) |
| ASUS             | AUS1643 | MB16ACM          | 1920x1080 | 15.3 | 2021 | [3EC0534B6D97](<Digital/ASUS/AUS1643/3EC0534B6D97>) |
| ASUS             | AUS1643 | MB16ACM          | 1920x1080 | 15.3 | 2020 | [949D0749441F](<Digital/ASUS/AUS1643/949D0749441F>) |
| ASUS             | AUS1645 | MB165B           | 1366x768  | 15.3 | 2020 | [43B3C5930092](<Digital/ASUS/AUS1645/43B3C5930092>) |
| ASUS             | AUS1646 | MB166C           | 1920x1080 | 15.3 | 2024 | [715A6587EECB](<Digital/ASUS/AUS1646/715A6587EECB>) |
| ASUS             | AUS1646 | MB166C           | 1920x1080 | 15.3 | 2023 | [914C0668D817](<Digital/ASUS/AUS1646/914C0668D817>) |
| ASUS             | AUS1647 | MB166CR          | 1920x1080 | 15.3 | 2024 | [38B27C033C3C](<Digital/ASUS/AUS1647/38B27C033C3C>) |
| ASUS             | AUS164A | MB169C+          | 1920x1080 | 15.3 | 2020 | [58F1314A4A8F](<Digital/ASUS/AUS164A/58F1314A4A8F>) |
| ASUS             | AUS164A | MB169C+          | 1920x1080 | 15.3 | 2019 | [D5E10469359F](<Digital/ASUS/AUS164A/D5E10469359F>) |
| ASUS             | AUS164B | MB16A            | 1920x1080 | 15.3 | 2022 | [B8D1283FE449](<Digital/ASUS/AUS164B/B8D1283FE449>) |
| ASUS             | AUS1661 | MB16AMT          | 1920x1080 | 15.3 | 2023 | [75CAAD2977F4](<Digital/ASUS/AUS1661/75CAAD2977F4>) |
| ASUS             | AUS1661 | MB16AMT          | 1920x1080 | 15.3 | 2022 | [020001DC1FD5](<Digital/ASUS/AUS1661/020001DC1FD5>) |
| ASUS             | AUS1661 | MB16AMT          | 1920x1080 | 15.3 | 2021 | [69E8F97B15E2](<Digital/ASUS/AUS1661/69E8F97B15E2>) |
| ASUS             | AUS1661 | MB16AMT          | 1920x1080 | 15.3 | 2020 | [2C002F8A61BB](<Digital/ASUS/AUS1661/2C002F8A61BB>) |
| ASUS             | AUS1661 | MB16AMT          | 1920x1080 | 15.3 | 2019 | [88CAF42147BD](<Digital/ASUS/AUS1661/88CAF42147BD>) |
| ASUS             | AUS1662 | MB16AHP          | 1920x1080 | 15.3 | 2023 | [6B1C6081A8E1](<Digital/ASUS/AUS1662/6B1C6081A8E1>) |
| ASUS             | AUS1662 | MB16AHP          | 1920x1080 | 15.3 | 2022 | [A4EF1F31CD9D](<Digital/ASUS/AUS1662/A4EF1F31CD9D>) |
| ASUS             | AUS1662 | MB16AHP          | 1920x1080 | 15.3 | 2021 | [35149BAE6DAB](<Digital/ASUS/AUS1662/35149BAE6DAB>) |
| ASUS             | AUS1662 | MB16AHP          | 1920x1080 | 15.3 | 2020 | [03A52B233E9F](<Digital/ASUS/AUS1662/03A52B233E9F>) |
| ASUS             | AUS1662 | MB16AHP          | 1920x1080 | 15.3 | 2019 | [2F8A323257C5](<Digital/ASUS/AUS1662/2F8A323257C5>) |
| ASUS             | AUS1663 | MB16AH           | 1920x1080 | 15.3 | 2022 | [F9A527247E80](<Digital/ASUS/AUS1663/F9A527247E80>) |
| ASUS             | AUS1663 | MB16AH           | 1920x1080 | 15.3 | 2021 | [31F97AE5568C](<Digital/ASUS/AUS1663/31F97AE5568C>) |
| ASUS             | AUS1663 | MB16AH           | 1920x1080 | 15.3 | 2020 | [0313C7545B88](<Digital/ASUS/AUS1663/0313C7545B88>) |
| ASUS             | AUS1664 | MB16AHG          | 1920x1080 | 15.3 | 2023 | [CEBD26F12051](<Digital/ASUS/AUS1664/CEBD26F12051>) |
| ASUS             | AUS1665 | MB16AMTR         | 1920x1080 | 15.3 | 2023 | [444A74D52DE2](<Digital/ASUS/AUS1665/444A74D52DE2>) |
| ASUS             | AUS16DA | MQ16AH           | 1920x1080 | 15.3 | 2023 | [A893E591EE56](<Digital/ASUS/AUS16DA/A893E591EE56>) |
| ASUS             | AUS16DA | MQ16AH           | 1920x1080 | 15.3 | 2022 | [22F3148BF7D9](<Digital/ASUS/AUS16DA/22F3148BF7D9>) |
| ASUS             | AUS16E1 | XG16A            | 1920x1080 | 15.3 | 2022 | [82A783DD69EB](<Digital/ASUS/AUS16E1/82A783DD69EB>) |
| ASUS             | AUS16E1 | XG16A            | 1920x1080 | 15.3 | 2021 | [4401CD9B7287](<Digital/ASUS/AUS16E1/4401CD9B7287>) |
| ASUS             | AUS16F3 | MB16QHG          | 2560x1600 | 16.3 | 2022 | [3326E9D3E31D](<Digital/ASUS/AUS16F3/3326E9D3E31D>) |
| ASUS             | AUS17E0 | XG17A            | 1920x1080 | 17.3 | 2022 | [199DC08B20CE](<Digital/ASUS/AUS17E0/199DC08B20CE>) |
| ASUS             | AUS17E0 | XG17A            | 1920x1080 | 17.3 | 2021 | [387A1D8C0B24](<Digital/ASUS/AUS17E0/387A1D8C0B24>) |
| ASUS             | AUS17E0 | XG17A            | 1920x1080 | 17.3 | 2020 | [350C34F75AD1](<Digital/ASUS/AUS17E0/350C34F75AD1>) |
| ASUS             | AUS17E0 |                  | 1920x1080 | 17.3 |      | [90E9719F7B2D](<Digital/ASUS/AUS17E0/90E9719F7B2D>) |
| ASUS             | AUS1B5E | XG27ACMG         | 2560x1440 | 27.2 | 2024 | [C8EAFE8885FB](<Digital/ASUS/AUS1B5E/C8EAFE8885FB>) |
| ASUS             | AUS2261 | MB229CF          | 1920x1080 | 21.7 | 2024 | [26E405CA2A14](<Digital/ASUS/AUS2261/26E405CA2A14>) |
| ASUS             | AUS22A1 | VP228            | 1920x1080 | 21.7 | 2022 | [009BB9B7F50F](<Digital/ASUS/AUS22A1/009BB9B7F50F>) |
| ASUS             | AUS22A1 | VP228            | 1920x1080 | 21.7 | 2020 | [133BDD313294](<Digital/ASUS/AUS22A1/133BDD313294>) |
| ASUS             | AUS22A1 | VP228            | 1920x1080 | 21.7 | 2019 | [3B28DC13F717](<Digital/ASUS/AUS22A1/3B28DC13F717>) |
| ASUS             | AUS22A1 | VP228            | 1920x1080 | 21.7 | 2018 | [4D276B6D6FE9](<Digital/ASUS/AUS22A1/4D276B6D6FE9>) |
| ASUS             | AUS22AA | VA229            | 1920x1080 | 21.7 | 2024 | [3E06BAFE263B](<Digital/ASUS/AUS22AA/3E06BAFE263B>) |
| ASUS             | AUS22AA | VA229            | 1920x1080 | 21.7 | 2022 | [02D6CEFC974A](<Digital/ASUS/AUS22AA/02D6CEFC974A>) |
| ASUS             | AUS22AA | VA229            | 1920x1080 | 21.7 | 2020 | [02CABD0170D9](<Digital/ASUS/AUS22AA/02CABD0170D9>) |
| ASUS             | AUS22C1 | VT229            | 1920x1080 | 21.7 | 2023 | [20F5D7CFADF3](<Digital/ASUS/AUS22C1/20F5D7CFADF3>) |
| ASUS             | AUS22C1 | VT229            | 1920x1080 | 21.7 | 2022 | [2D9D10E2CF64](<Digital/ASUS/AUS22C1/2D9D10E2CF64>) |
| ASUS             | AUS22C1 | VT229            | 1920x1080 | 21.7 | 2021 | [94504FD5EAE2](<Digital/ASUS/AUS22C1/94504FD5EAE2>) |
| ASUS             | AUS22C1 | VT229            | 1920x1080 | 21.7 | 2020 | [0015126D1D03](<Digital/ASUS/AUS22C1/0015126D1D03>) |
| ASUS             | AUS22C1 | VT229            | 1920x1080 | 21.7 | 2019 | [27119E74BE2F](<Digital/ASUS/AUS22C1/27119E74BE2F>) |
| ASUS             | AUS22C1 | VT229            | 1920x1080 | 21.7 | 2018 | [716DB65E33CE](<Digital/ASUS/AUS22C1/716DB65E33CE>) |
| ASUS             | AUS22CC | VZ229            | 1920x1080 | 21.7 | 2021 | [14D57D84AB2E](<Digital/ASUS/AUS22CC/14D57D84AB2E>) |
| ASUS             | AUS22CC | VZ229            | 1920x1080 | 21.7 | 2020 | [656E8FEFE6F3](<Digital/ASUS/AUS22CC/656E8FEFE6F3>) |
| ASUS             | AUS22CC | VZ229            | 1920x1080 | 21.7 | 2019 | [1D0A2D3D0AFD](<Digital/ASUS/AUS22CC/1D0A2D3D0AFD>) |
| ASUS             | AUS22CC | VZ229            | 1920x1080 | 21.7 | 2018 | [0B225716B9F5](<Digital/ASUS/AUS22CC/0B225716B9F5>) |
| ASUS             | AUS22CC | VZ229            | 1920x1080 | 21.7 | 2017 | [0DBF011E1FB9](<Digital/ASUS/AUS22CC/0DBF011E1FB9>) |
| ASUS             | AUS22CC | VZ229            | 1920x1080 | 21.7 | 2016 | [124397553C39](<Digital/ASUS/AUS22CC/124397553C39>) |
| ASUS             | AUS22D3 | VY229HF          | 1920x1080 | 21.5 | 2024 | [E34C36C64B11](<Digital/ASUS/AUS22D3/E34C36C64B11>) |
| ASUS             | AUS22D4 | VP228HE          | 1920x1080 | 21.7 | 2022 | [8B9484D4E8EA](<Digital/ASUS/AUS22D4/8B9484D4E8EA>) |
| ASUS             | AUS22D4 | VP228HE          | 1920x1080 | 21.7 | 2021 | [DE90232E140E](<Digital/ASUS/AUS22D4/DE90232E140E>) |
| ASUS             | AUS22D6 | VP229HE          | 1920x1080 | 21.7 | 2023 | [3D80DA87248B](<Digital/ASUS/AUS22D6/3D80DA87248B>) |
| ASUS             | AUS22D8 | VZ22EHE          | 1920x1080 | 21.5 | 2023 | [0F6AE0737CA5](<Digital/ASUS/AUS22D8/0F6AE0737CA5>) |
| ASUS             | AUS22DA | VP229            | 1920x1080 | 21.7 | 2022 | [6A24D3DE9520](<Digital/ASUS/AUS22DA/6A24D3DE9520>) |
| ASUS             | AUS22DA | VP229            | 1920x1080 | 21.7 | 2021 | [05F20943A191](<Digital/ASUS/AUS22DA/05F20943A191>) |
| ASUS             | AUS22DA | VP229            | 1920x1080 | 21.7 | 2020 | [086701F3077F](<Digital/ASUS/AUS22DA/086701F3077F>) |
| ASUS             | AUS22DB | VP229            | 1920x1080 | 21.7 | 2024 | [58F58F855DC6](<Digital/ASUS/AUS22DB/58F58F855DC6>) |
| ASUS             | AUS22DB | VP229            | 1920x1080 | 21.7 | 2022 | [7A6BB941D0C9](<Digital/ASUS/AUS22DB/7A6BB941D0C9>) |
| ASUS             | AUS22DB | VP229            | 1920x1080 | 21.7 | 2020 | [9A3376A9AEE8](<Digital/ASUS/AUS22DB/9A3376A9AEE8>) |
| ASUS             | AUS22DC | VY229HE          | 1920x1080 | 21.5 | 2024 | [4E359EA7417D](<Digital/ASUS/AUS22DC/4E359EA7417D>) |
| ASUS             | AUS22DC | VY229HE          | 1920x1080 | 21.5 | 2023 | [2177EDA5068A](<Digital/ASUS/AUS22DC/2177EDA5068A>) |
| ASUS             | AUS22F1 | VA229            | 1920x1080 | 21.7 | 2018 | [016347532809](<Digital/ASUS/AUS22F1/016347532809>) |
| ASUS             | AUS22F2 | VA229            | 1920x1080 | 21.7 | 2019 | [7FCB89342349](<Digital/ASUS/AUS22F2/7FCB89342349>) |
| ASUS             | AUS22F2 | VA229            | 1920x1080 | 21.7 | 2018 | [C1D20859403D](<Digital/ASUS/AUS22F2/C1D20859403D>) |
| ASUS             | AUS22F3 | VA229            | 1920x1080 | 21.7 | 2022 | [3E8046015592](<Digital/ASUS/AUS22F3/3E8046015592>) |
| ASUS             | AUS22F3 | VA229            | 1920x1080 | 21.7 | 2021 | [8840CA93E6C4](<Digital/ASUS/AUS22F3/8840CA93E6C4>) |
| ASUS             | AUS22F3 | VA229            | 1920x1080 | 21.7 | 2020 | [B7AADE3B37D0](<Digital/ASUS/AUS22F3/B7AADE3B37D0>) |
| ASUS             | AUS22F3 | VA229            | 1920x1080 | 21.7 | 2019 | [3EAB85D81BC1](<Digital/ASUS/AUS22F3/3EAB85D81BC1>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2022 | [7268E90BCCF5](<Digital/ASUS/AUS23CC/7268E90BCCF5>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2021 | [370D124D2C9B](<Digital/ASUS/AUS23CC/370D124D2C9B>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2020 | [0E7CBFAD72AC](<Digital/ASUS/AUS23CC/0E7CBFAD72AC>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2019 | [63A92CB8F031](<Digital/ASUS/AUS23CC/63A92CB8F031>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2018 | [02B068D1BD99](<Digital/ASUS/AUS23CC/02B068D1BD99>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2017 | [0F5727FD281A](<Digital/ASUS/AUS23CC/0F5727FD281A>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 | 2016 | [07A7B2869F83](<Digital/ASUS/AUS23CC/07A7B2869F83>) |
| ASUS             | AUS23CC | VZ239            | 1920x1080 | 23.1 |      | [27204C2806E1](<Digital/ASUS/AUS23CC/27204C2806E1>) |
| ASUS             | AUS2400 | PA248QV          | 1920x1200 | 24.0 | 2025 | [6653455B17D7](<Digital/ASUS/AUS2400/6653455B17D7>) |
| ASUS             | AUS2400 | PA248QV          | 1920x1200 | 24.0 | 2023 | [4CBB4D3FB72D](<Digital/ASUS/AUS2400/4CBB4D3FB72D>) |
| ASUS             | AUS2400 | PA248QV          | 1920x1200 | 24.0 | 2022 | [69F2CD90B602](<Digital/ASUS/AUS2400/69F2CD90B602>) |
| ASUS             | AUS2400 | PA248QV          | 1920x1200 | 24.0 | 2021 | [0F607081DA73](<Digital/ASUS/AUS2400/0F607081DA73>) |
| ASUS             | AUS2400 | PA248QV          | 1920x1200 | 24.0 | 2020 | [0B33F04F6CC7](<Digital/ASUS/AUS2400/0B33F04F6CC7>) |
| ASUS             | AUS2400 | PA248QV          | 1920x1200 | 24.0 |      | [76FDE3EA52AB](<Digital/ASUS/AUS2400/76FDE3EA52AB>) |
| ASUS             | AUS2401 | VG249Q1R         | 1920x1080 | 23.4 | 2024 | [30C245BB06A7](<Digital/ASUS/AUS2401/30C245BB06A7>) |
| ASUS             | AUS2401 | VG249Q1R         | 1920x1080 | 23.4 | 2023 | [05B47FAF64E1](<Digital/ASUS/AUS2401/05B47FAF64E1>) |
| ASUS             | AUS2401 | VG249Q1R         | 1920x1080 | 23.4 | 2022 | [5A0A7C8470E7](<Digital/ASUS/AUS2401/5A0A7C8470E7>) |
| ASUS             | AUS2401 | VG249Q1R         | 1920x1080 | 23.4 | 2021 | [661492B0BEF5](<Digital/ASUS/AUS2401/661492B0BEF5>) |
| ASUS             | AUS2401 | VG249Q1R         | 1920x1080 | 23.4 | 2020 | [14B933A8C153](<Digital/ASUS/AUS2401/14B933A8C153>) |
| ASUS             | AUS2402 | VA24D            | 1920x1080 | 24.0 | 2023 | [649407BC0DB1](<Digital/ASUS/AUS2402/649407BC0DB1>) |
| ASUS             | AUS2402 | VA24D            | 1920x1080 | 24.0 | 2022 | [2F491448FF92](<Digital/ASUS/AUS2402/2F491448FF92>) |
| ASUS             | AUS2402 | VA24D            | 1920x1080 | 24.0 | 2021 | [0369BC2BB995](<Digital/ASUS/AUS2402/0369BC2BB995>) |
| ASUS             | AUS2402 | VA24D            | 1920x1080 | 24.0 | 2020 | [B96B8C33F086](<Digital/ASUS/AUS2402/B96B8C33F086>) |
| ASUS             | AUS2403 | VA24D            | 1920x1080 | 24.0 | 2025 | [E1EB0EC3B321](<Digital/ASUS/AUS2403/E1EB0EC3B321>) |
| ASUS             | AUS2403 | VA24D            | 1920x1080 | 24.0 | 2024 | [2CB8158A3616](<Digital/ASUS/AUS2403/2CB8158A3616>) |
| ASUS             | AUS2403 | VA24D            | 1920x1080 | 24.0 | 2023 | [5178B076D3FB](<Digital/ASUS/AUS2403/5178B076D3FB>) |
| ASUS             | AUS2403 | VA24D            | 1920x1080 | 24.0 | 2022 | [2F6F5715CAF6](<Digital/ASUS/AUS2403/2F6F5715CAF6>) |
| ASUS             | AUS2403 | VA24D            | 1920x1080 | 24.0 | 2021 | [1910081DF353](<Digital/ASUS/AUS2403/1910081DF353>) |
| ASUS             | AUS2403 | VA24D            | 1920x1080 | 24.0 | 2020 | [0356CA9C1B9B](<Digital/ASUS/AUS2403/0356CA9C1B9B>) |
| ASUS             | AUS2404 | VZ249HEG1R       | 1920x1080 | 23.4 | 2021 | [87EFB6A5D072](<Digital/ASUS/AUS2404/87EFB6A5D072>) |
| ASUS             | AUS2404 | VZ249HEG1R       | 1920x1080 | 23.4 | 2020 | [021271D8645C](<Digital/ASUS/AUS2404/021271D8645C>) |
| ASUS             | AUS2405 | VG24VQR          | 1920x1080 | 23.4 | 2022 | [058065B5FE98](<Digital/ASUS/AUS2405/058065B5FE98>) |
| ASUS             | AUS2406 | VG24VQE          | 1920x1080 | 23.4 | 2023 | [0264FA215E76](<Digital/ASUS/AUS2406/0264FA215E76>) |
| ASUS             | AUS2406 | VG24VQE          | 1920x1080 | 23.4 | 2022 | [46276C87F5F4](<Digital/ASUS/AUS2406/46276C87F5F4>) |
| ASUS             | AUS2406 | VG24VQE          | 1920x1080 | 23.4 | 2021 | [2931068F4660](<Digital/ASUS/AUS2406/2931068F4660>) |
| ASUS             | AUS2407 | C1241Q           | 1920x1080 | 24.0 | 2024 | [412D1338E179](<Digital/ASUS/AUS2407/412D1338E179>) |
| ASUS             | AUS240B | VA24D            | 1920x1080 | 24.0 | 2021 | [83B3B8B7C6BC](<Digital/ASUS/AUS240B/83B3B8B7C6BC>) |
| ASUS             | AUS240C | VA24D            | 1920x1080 | 24.0 | 2021 | [4826969386AE](<Digital/ASUS/AUS240C/4826969386AE>) |
| ASUS             | AUS2420 | VG24V            | 1920x1080 | 23.4 | 2022 | [672C856555FC](<Digital/ASUS/AUS2420/672C856555FC>) |
| ASUS             | AUS2420 | VG24V            | 1920x1080 | 23.4 | 2021 | [01861181F72A](<Digital/ASUS/AUS2420/01861181F72A>) |
| ASUS             | AUS2420 | VG24V            | 1920x1080 | 23.4 | 2020 | [00C985CDF705](<Digital/ASUS/AUS2420/00C985CDF705>) |
| ASUS             | AUS2420 | VG24V            | 1920x1080 | 23.4 | 2019 | [071FB18CD90D](<Digital/ASUS/AUS2420/071FB18CD90D>) |
| ASUS             | AUS2421 | VG249            | 1920x1080 | 24.0 | 2023 | [48EFE8BEC636](<Digital/ASUS/AUS2421/48EFE8BEC636>) |
| ASUS             | AUS2421 | VG249            | 1920x1080 | 24.0 | 2022 | [031A5D3683C9](<Digital/ASUS/AUS2421/031A5D3683C9>) |
| ASUS             | AUS2421 | VG249            | 1920x1080 | 24.0 | 2021 | [0A20A5433FC0](<Digital/ASUS/AUS2421/0A20A5433FC0>) |
| ASUS             | AUS2421 | VG249            | 1920x1080 | 24.0 | 2020 | [05F967DA909F](<Digital/ASUS/AUS2421/05F967DA909F>) |
| ASUS             | AUS2421 | VG24V            | 1920x1080 | 23.4 | 2020 | [A18C9FBB89AB](<Digital/ASUS/AUS2421/A18C9FBB89AB>) |
| ASUS             | AUS2421 | VG249            | 1920x1080 | 24.0 | 2019 | [26F524640248](<Digital/ASUS/AUS2421/26F524640248>) |
| ASUS             | AUS2421 |                  | 1920x1080 | 24.0 |      | [894B27B2E7A0](<Digital/ASUS/AUS2421/894B27B2E7A0>) |
| ASUS             | AUS2426 | VA24EQSB         | 1920x1080 | 24.0 | 2025 | [5649967DE6D8](<Digital/ASUS/AUS2426/5649967DE6D8>) |
| ASUS             | AUS2426 | VA24EQSB         | 1920x1080 | 24.0 | 2024 | [9DA6CCF14441](<Digital/ASUS/AUS2426/9DA6CCF14441>) |
| ASUS             | AUS2428 | VG249QM1A        | 1920x1080 | 24.0 | 2023 | [04BED15EBC24](<Digital/ASUS/AUS2428/04BED15EBC24>) |
| ASUS             | AUS2429 | VG246H1A         | 1920x1080 | 24.0 | 2024 | [BABFCC753F3C](<Digital/ASUS/AUS2429/BABFCC753F3C>) |
| ASUS             | AUS2429 | VG246H1A         | 1920x1080 | 24.0 | 2023 | [B351BB3572BA](<Digital/ASUS/AUS2429/B351BB3572BA>) |
| ASUS             | AUS242A | VG249Q1A         | 1920x1080 | 23.4 | 2023 | [0E8C6B73EE13](<Digital/ASUS/AUS242A/0E8C6B73EE13>) |
| ASUS             | AUS242A | VG249Q1A         | 1920x1080 | 23.4 | 2022 | [4BB5F52FA223](<Digital/ASUS/AUS242A/4BB5F52FA223>) |
| ASUS             | AUS242A | VG249Q1A         | 1920x1080 | 23.4 | 2021 | [0EC9163C2A16](<Digital/ASUS/AUS242A/0EC9163C2A16>) |
| ASUS             | AUS242A | VG249Q1A         | 1920x1080 | 23.4 | 2020 | [4D9E8D099DEA](<Digital/ASUS/AUS242A/4D9E8D099DEA>) |
| ASUS             | AUS242B | VG247Q1A         | 1920x1080 | 24.0 | 2024 | [4E7507CDF8FA](<Digital/ASUS/AUS242B/4E7507CDF8FA>) |
| ASUS             | AUS242B | VG247Q1A         | 1920x1080 | 24.0 | 2023 | [0097C0F368F1](<Digital/ASUS/AUS242B/0097C0F368F1>) |
| ASUS             | AUS242B | VG247Q1A         | 1920x1080 | 24.0 | 2022 | [4B1BE4E1DD85](<Digital/ASUS/AUS242B/4B1BE4E1DD85>) |
| ASUS             | AUS242B | VG247Q1A         | 1920x1080 | 24.0 | 2021 | [2D018FA8AFED](<Digital/ASUS/AUS242B/2D018FA8AFED>) |
| ASUS             | AUS242B | VG247Q1A         | 3840x2160 | 24.0 | 2021 | [BCC3DFE287E3](<Digital/ASUS/AUS242B/BCC3DFE287E3>) |
| ASUS             | AUS242C | VG24VQ1B         | 1920x1080 | 24.0 | 2022 | [42445AA8AB74](<Digital/ASUS/AUS242C/42445AA8AB74>) |
| ASUS             | AUS242C | VG24VQ1B         | 1920x1080 | 24.0 | 2021 | [94A4FF2361B9](<Digital/ASUS/AUS242C/94A4FF2361B9>) |
| ASUS             | AUS242E | VG248Q1B         | 1920x1080 | 24.0 | 2022 | [FC500A84708F](<Digital/ASUS/AUS242E/FC500A84708F>) |
| ASUS             | AUS242F | VG249QM1A        | 1920x1080 | 24.0 | 2025 | [374934106037](<Digital/ASUS/AUS242F/374934106037>) |
| ASUS             | AUS242F | VG249QM1A        | 1920x1080 | 24.0 | 2024 | [667E3D25B4AF](<Digital/ASUS/AUS242F/667E3D25B4AF>) |
| ASUS             | AUS242F | VG249QM1A        | 1920x1080 | 24.0 | 2023 | [57AFCA2C1280](<Digital/ASUS/AUS242F/57AFCA2C1280>) |
| ASUS             | AUS2445 | VA24EHF          | 1920x1080 | 24.0 | 2022 | [1099D787B1B8](<Digital/ASUS/AUS2445/1099D787B1B8>) |
| ASUS             | AUS2460 | VA24DCP          | 1920x1080 | 24.2 | 2023 | [62ED52FF7351](<Digital/ASUS/AUS2460/62ED52FF7351>) |
| ASUS             | AUS2460 | VA24DCP          | 1920x1080 | 24.2 | 2022 | [436458064678](<Digital/ASUS/AUS2460/436458064678>) |
| ASUS             | AUS2460 | VA24DCP          | 1920x1080 | 24.2 | 2021 | [D518868E922E](<Digital/ASUS/AUS2460/D518868E922E>) |
| ASUS             | AUS2462 | PA24A            | 1920x1200 | 24.0 | 2020 | [1E75BAD9109B](<Digital/ASUS/AUS2462/1E75BAD9109B>) |
| ASUS             | AUS2463 | PA247CV          | 1920x1080 | 24.0 | 2023 | [734F51C6ECEA](<Digital/ASUS/AUS2463/734F51C6ECEA>) |
| ASUS             | AUS2463 | PA247CV          | 1920x1080 | 24.0 | 2021 | [148DF7DAD1F6](<Digital/ASUS/AUS2463/148DF7DAD1F6>) |
| ASUS             | AUS2463 | PA247CV          | 1920x1080 | 24.0 | 2020 | [AA6F077071D8](<Digital/ASUS/AUS2463/AA6F077071D8>) |
| ASUS             | AUS2464 | PA247CV          | 1920x1080 | 24.0 | 2024 | [41281DF1C902](<Digital/ASUS/AUS2464/41281DF1C902>) |
| ASUS             | AUS2464 | PA247CV          | 1920x1080 | 24.0 | 2022 | [3DD28A08D564](<Digital/ASUS/AUS2464/3DD28A08D564>) |
| ASUS             | AUS2464 | PA247CV          | 1920x1080 | 24.0 | 2021 | [137D0B8B24F0](<Digital/ASUS/AUS2464/137D0B8B24F0>) |
| ASUS             | AUS2465 | VA24DCP          | 1920x1080 | 24.2 | 2022 | [1767D2DE9D39](<Digital/ASUS/AUS2465/1767D2DE9D39>) |
| ASUS             | AUS2467 | PA248CNV         | 1920x1200 | 24.0 | 2022 | [561891C6C3EC](<Digital/ASUS/AUS2467/561891C6C3EC>) |
| ASUS             | AUS246C | PA24ACRV         | 2560x1440 | 27.2 | 2024 | [2EDD4652D589](<Digital/ASUS/AUS246C/2EDD4652D589>) |
| ASUS             | AUS246E | BE24ECSNK        | 1920x1080 | 24.0 | 2022 | [FBA4294FBB9A](<Digital/ASUS/AUS246E/FBA4294FBB9A>) |
| ASUS             | AUS2480 | BE24E            | 1920x1080 | 24.0 | 2023 | [6211FAE50FCA](<Digital/ASUS/AUS2480/6211FAE50FCA>) |
| ASUS             | AUS2480 | BE24E            | 1920x1080 | 24.0 | 2022 | [CE45BA1B4485](<Digital/ASUS/AUS2480/CE45BA1B4485>) |
| ASUS             | AUS2481 | VA24DQLB         | 1920x1080 | 24.0 | 2021 | [67E9539D7011](<Digital/ASUS/AUS2481/67E9539D7011>) |
| ASUS             | AUS2481 | VA24DQLB         | 1920x1080 | 24.0 | 2020 | [2A0A9134F33E](<Digital/ASUS/AUS2481/2A0A9134F33E>) |
| ASUS             | AUS2482 | VA24DQLB         | 1920x1080 | 24.0 | 2022 | [C08A263026AB](<Digital/ASUS/AUS2482/C08A263026AB>) |
| ASUS             | AUS2482 | VA24DQLB         | 1920x1080 | 24.0 | 2021 | [6DBFBDF6AA75](<Digital/ASUS/AUS2482/6DBFBDF6AA75>) |
| ASUS             | AUS2482 | VA24DQLB         | 1920x1080 | 24.0 | 2020 | [3A22FD7DD357](<Digital/ASUS/AUS2482/3A22FD7DD357>) |
| ASUS             | AUS2483 | BE24EQK          | 1920x1080 | 24.0 | 2021 | [EC4ACD8004DF](<Digital/ASUS/AUS2483/EC4ACD8004DF>) |
| ASUS             | AUS2483 | BE24EQK          | 1920x1080 | 24.0 | 2020 | [790EB99104C4](<Digital/ASUS/AUS2483/790EB99104C4>) |
| ASUS             | AUS2485 | BE24EQSK         | 1920x1080 | 24.0 | 2021 | [0C143D27521E](<Digital/ASUS/AUS2485/0C143D27521E>) |
| ASUS             | AUS2487 | PA248QV          | 1920x1200 | 24.0 | 2024 | [3F8710A99F3B](<Digital/ASUS/AUS2487/3F8710A99F3B>) |
| ASUS             | AUS2487 | PA248QV          | 1920x1200 | 24.0 | 2023 | [08D707F71056](<Digital/ASUS/AUS2487/08D707F71056>) |
| ASUS             | AUS2487 | PA248QV          | 1920x1200 | 24.0 | 2022 | [EC280A15BF30](<Digital/ASUS/AUS2487/EC280A15BF30>) |
| ASUS             | AUS2487 | PA248QV          | 1920x1200 | 24.0 | 2021 | [2B473481CAE6](<Digital/ASUS/AUS2487/2B473481CAE6>) |
| ASUS             | AUS2487 | PA248QV          | 1920x1200 | 24.0 | 2020 | [02CA6E9FF896](<Digital/ASUS/AUS2487/02CA6E9FF896>) |
| ASUS             | AUS2487 | PA248QV          | 1920x1200 | 24.0 |      | [2E851C7308D0](<Digital/ASUS/AUS2487/2E851C7308D0>) |
| ASUS             | AUS2489 | VG249Q3A         | 1920x1080 | 24.0 | 2025 | [7D30D7A67777](<Digital/ASUS/AUS2489/7D30D7A67777>) |
| ASUS             | AUS2489 | VG249Q3A         | 1920x1080 | 24.0 | 2024 | [0B6D4A076B39](<Digital/ASUS/AUS2489/0B6D4A076B39>) |
| ASUS             | AUS248A | MB249C           | 1920x1080 | 24.0 | 2024 | [76CEA1FB0EE9](<Digital/ASUS/AUS248A/76CEA1FB0EE9>) |
| ASUS             | AUS24A0 | VG249QL3A        | 1920x1080 | 24.0 | 2024 | [43EC0F296302](<Digital/ASUS/AUS24A0/43EC0F296302>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 | 2021 | [07B984801CB0](<Digital/ASUS/AUS24A1/07B984801CB0>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 | 2020 | [1A61CC7B7E27](<Digital/ASUS/AUS24A1/1A61CC7B7E27>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 | 2019 | [0AF068D48A3A](<Digital/ASUS/AUS24A1/0AF068D48A3A>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 | 2018 | [0810D584DBB6](<Digital/ASUS/AUS24A1/0810D584DBB6>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 | 2017 | [03E8DB3B3C2E](<Digital/ASUS/AUS24A1/03E8DB3B3C2E>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 | 2016 | [01570396E6F7](<Digital/ASUS/AUS24A1/01570396E6F7>) |
| ASUS             | AUS24A1 | VG245            | 1920x1080 | 24.0 |      | [0E773D0AE679](<Digital/ASUS/AUS24A1/0E773D0AE679>) |
| ASUS             | AUS24A2 | VG245            | 1920x1080 | 24.0 |      | [80355082CC5B](<Digital/ASUS/AUS24A2/80355082CC5B>) |
| ASUS             | AUS24A3 | VG245            | 1920x1080 | 24.0 | 2020 | [2D44D87CA1D1](<Digital/ASUS/AUS24A3/2D44D87CA1D1>) |
| ASUS             | AUS24A3 | MG248            | 1920x1080 | 24.0 | 2019 | [19C2C69FB9D4](<Digital/ASUS/AUS24A3/19C2C69FB9D4>) |
| ASUS             | AUS24A3 | MG248            | 1920x1080 | 24.0 | 2018 | [3B59E74D7041](<Digital/ASUS/AUS24A3/3B59E74D7041>) |
| ASUS             | AUS24A3 | MG248            | 1920x1080 | 24.0 | 2017 | [3D517BF848FB](<Digital/ASUS/AUS24A3/3D517BF848FB>) |
| ASUS             | AUS24A4 | MG248            | 1920x1080 | 24.0 | 2020 | [2509633AC08A](<Digital/ASUS/AUS24A4/2509633AC08A>) |
| ASUS             | AUS24A4 | MG248            | 1920x1080 | 24.0 | 2019 | [774F151898CF](<Digital/ASUS/AUS24A4/774F151898CF>) |
| ASUS             | AUS24A4 | MG248            | 1920x1080 | 24.0 | 2018 | [4BDCAB7F658B](<Digital/ASUS/AUS24A4/4BDCAB7F658B>) |
| ASUS             | AUS24A4 | MG248            | 1920x1080 | 24.0 | 2017 | [2B7A2BB2F9B5](<Digital/ASUS/AUS24A4/2B7A2BB2F9B5>) |
| ASUS             | AUS24A5 | BE24D            | 1920x1080 | 24.0 | 2019 | [DCB5E9810E57](<Digital/ASUS/AUS24A5/DCB5E9810E57>) |
| ASUS             | AUS24A5 | BE24D            | 1920x1080 | 24.0 | 2018 | [6500A510AFE7](<Digital/ASUS/AUS24A5/6500A510AFE7>) |
| ASUS             | AUS24A7 | VL249HE          | 1920x1080 | 24.0 | 2021 | [1B445716C0B3](<Digital/ASUS/AUS24A7/1B445716C0B3>) |
| ASUS             | AUS24A7 | VL249HE          | 1920x1080 | 24.0 | 2020 | [46D73244DBC0](<Digital/ASUS/AUS24A7/46D73244DBC0>) |
| ASUS             | AUS24A7 | VL249HE          | 1920x1080 | 24.0 | 2019 | [BFA82CDA87AA](<Digital/ASUS/AUS24A7/BFA82CDA87AA>) |
| ASUS             | AUS24A8 | PB247            | 1920x1080 | 24.0 | 2019 | [CC089EAF22DD](<Digital/ASUS/AUS24A8/CC089EAF22DD>) |
| ASUS             | AUS24A8 | PB247            | 1920x1080 | 24.0 | 2018 | [192ECAB8CE51](<Digital/ASUS/AUS24A8/192ECAB8CE51>) |
| ASUS             | AUS24A9 | VP248QG          | 1920x1080 | 24.0 | 2022 | [3F208D8D488E](<Digital/ASUS/AUS24A9/3F208D8D488E>) |
| ASUS             | AUS24A9 | VP248QG          | 1920x1080 | 24.0 | 2021 | [1853277D88C5](<Digital/ASUS/AUS24A9/1853277D88C5>) |
| ASUS             | AUS24A9 | VP248QG          | 1920x1080 | 24.0 | 2020 | [2AD21C5588FF](<Digital/ASUS/AUS24A9/2AD21C5588FF>) |
| ASUS             | AUS24A9 | VP248QG          | 1920x1080 | 24.0 | 2019 | [121820CEB8D6](<Digital/ASUS/AUS24A9/121820CEB8D6>) |
| ASUS             | AUS24A9 | VP248QG          | 1920x1080 | 24.0 | 2018 | [0E1D9368E42D](<Digital/ASUS/AUS24A9/0E1D9368E42D>) |
| ASUS             | AUS24AA | VP249            | 1920x1080 | 24.0 | 2021 | [152EBAF5CC3E](<Digital/ASUS/AUS24AA/152EBAF5CC3E>) |
| ASUS             | AUS24AA | VP249            | 1920x1080 | 24.0 | 2020 | [0B2EEB7888FC](<Digital/ASUS/AUS24AA/0B2EEB7888FC>) |
| ASUS             | AUS24AA | VP249            | 1920x1080 | 24.0 | 2019 | [084E1B6364F3](<Digital/ASUS/AUS24AA/084E1B6364F3>) |
| ASUS             | AUS24AA | VP249            | 1920x1080 | 24.0 | 2018 | [6C30F52B93A3](<Digital/ASUS/AUS24AA/6C30F52B93A3>) |
| ASUS             | AUS24AA | VP249            | 1920x1080 | 24.0 | 2017 | [62C5AC6B6645](<Digital/ASUS/AUS24AA/62C5AC6B6645>) |
| ASUS             | AUS24AA |                  | 1920x1080 | 24.0 |      | [DF681CDC511E](<Digital/ASUS/AUS24AA/DF681CDC511E>) |
| ASUS             | AUS24AB | VG248            | 1920x1080 | 24.0 | 2019 | [0665919DDB3A](<Digital/ASUS/AUS24AB/0665919DDB3A>) |
| ASUS             | AUS24AB | VG248            | 1920x1080 | 24.0 | 2018 | [0F43037E355D](<Digital/ASUS/AUS24AB/0F43037E355D>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 | 2024 | [A845C10D57D7](<Digital/ASUS/AUS24AC/A845C10D57D7>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 | 2023 | [4EBE4261E975](<Digital/ASUS/AUS24AC/4EBE4261E975>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 | 2022 | [5D63E540BA5F](<Digital/ASUS/AUS24AC/5D63E540BA5F>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 | 2021 | [028E086B69B7](<Digital/ASUS/AUS24AC/028E086B69B7>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 | 2020 | [1A311E11F569](<Digital/ASUS/AUS24AC/1A311E11F569>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 | 2019 | [EBBCD4757308](<Digital/ASUS/AUS24AC/EBBCD4757308>) |
| ASUS             | AUS24AC | VG248            | 1920x1080 | 24.0 |      | [46936A80D5A4](<Digital/ASUS/AUS24AC/46936A80D5A4>) |
| ASUS             | AUS24AD | BE24W            | 1920x1200 | 24.0 | 2022 | [0A78B98F7D48](<Digital/ASUS/AUS24AD/0A78B98F7D48>) |
| ASUS             | AUS24AF | VP249            | 1920x1080 | 24.0 | 2022 | [16D89ECB76FD](<Digital/ASUS/AUS24AF/16D89ECB76FD>) |
| ASUS             | AUS24AF | VP249            | 1920x1080 | 24.0 | 2021 | [00B0E299AEE3](<Digital/ASUS/AUS24AF/00B0E299AEE3>) |
| ASUS             | AUS24AF | VP249            | 1920x1080 | 24.0 | 2020 | [04195C1E73C5](<Digital/ASUS/AUS24AF/04195C1E73C5>) |
| ASUS             | AUS24AF | VP249            | 1920x1080 | 24.0 | 2019 | [524FC4F065FD](<Digital/ASUS/AUS24AF/524FC4F065FD>) |
| ASUS             | AUS24AF |                  | 1920x1080 | 24.0 |      | [9A7C9D90A81A](<Digital/ASUS/AUS24AF/9A7C9D90A81A>) |
| ASUS             | AUS24B1 | ROG PG248Q       | 1920x1080 | 24.0 | 2019 | [167D60C02C0A](<Digital/ASUS/AUS24B1/167D60C02C0A>) |
| ASUS             | AUS24B1 | ROG PG248Q       | 1920x1080 | 24.0 | 2017 | [654915CA00BB](<Digital/ASUS/AUS24B1/654915CA00BB>) |
| ASUS             | AUS24B1 | ROG PG248Q       | 1920x1080 | 24.0 | 2016 | [197FEDB2A950](<Digital/ASUS/AUS24B1/197FEDB2A950>) |
| ASUS             | AUS24B2 | ROG PG248Q       | 1920x1080 | 24.0 | 2020 | [A28050925323](<Digital/ASUS/AUS24B2/A28050925323>) |
| ASUS             | AUS24B2 | ROG PG248Q       | 1920x1080 | 24.0 | 2018 | [5798487709AB](<Digital/ASUS/AUS24B2/5798487709AB>) |
| ASUS             | AUS24B2 | ROG PG248Q       | 1920x1080 | 24.0 | 2016 | [820B5CC46633](<Digital/ASUS/AUS24B2/820B5CC46633>) |
| ASUS             | AUS24B3 | XG248Q           | 1920x1080 | 24.0 | 2020 | [A9A899A6ECAA](<Digital/ASUS/AUS24B3/A9A899A6ECAA>) |
| ASUS             | AUS24B3 | XG248Q           | 1920x1080 | 24.0 | 2019 | [442CD2878048](<Digital/ASUS/AUS24B3/442CD2878048>) |
| ASUS             | AUS24C1 | VA249            | 1920x1080 | 24.0 | 2022 | [3C49890F6538](<Digital/ASUS/AUS24C1/3C49890F6538>) |
| ASUS             | AUS24C1 | VA249            | 1920x1080 | 24.0 | 2021 | [47DC86E22280](<Digital/ASUS/AUS24C1/47DC86E22280>) |
| ASUS             | AUS24C1 | VA249            | 1920x1080 | 24.0 | 2020 | [11C71D0C7AA0](<Digital/ASUS/AUS24C1/11C71D0C7AA0>) |
| ASUS             | AUS24C1 | VA249            | 1920x1080 | 24.0 | 2019 | [064A31080FC3](<Digital/ASUS/AUS24C1/064A31080FC3>) |
| ASUS             | AUS24C1 | VA249            | 1920x1080 | 24.0 | 2018 | [15A79AA749CE](<Digital/ASUS/AUS24C1/15A79AA749CE>) |
| ASUS             | AUS24C1 | VA249            | 1920x1080 | 24.0 | 2017 | [251B1E0BF37F](<Digital/ASUS/AUS24C1/251B1E0BF37F>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 | 2023 | [04F7C85C771E](<Digital/ASUS/AUS24C2/04F7C85C771E>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 | 2022 | [12E53C4B91C9](<Digital/ASUS/AUS24C2/12E53C4B91C9>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 | 2021 | [29A5566C522A](<Digital/ASUS/AUS24C2/29A5566C522A>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 | 2020 | [06DB9C0B1BBE](<Digital/ASUS/AUS24C2/06DB9C0B1BBE>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 | 2019 | [A3393C6A6DDB](<Digital/ASUS/AUS24C2/A3393C6A6DDB>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 | 2017 | [7DDA100D6649](<Digital/ASUS/AUS24C2/7DDA100D6649>) |
| ASUS             | AUS24C2 | VG248            | 1920x1080 | 24.0 |      | [6407DD05545A](<Digital/ASUS/AUS24C2/6407DD05545A>) |
| ASUS             | AUS24C3 | VG246            | 1920x1080 | 24.0 | 2022 | [82C1E287C8FF](<Digital/ASUS/AUS24C3/82C1E287C8FF>) |
| ASUS             | AUS24C3 | VG246            | 1920x1080 | 24.0 | 2021 | [A0F23C4A1811](<Digital/ASUS/AUS24C3/A0F23C4A1811>) |
| ASUS             | AUS24C3 | VG246            | 1920x1080 | 24.0 | 2020 | [30673F2A5DC8](<Digital/ASUS/AUS24C3/30673F2A5DC8>) |
| ASUS             | AUS24CA | VP247            | 1920x1080 | 23.4 | 2020 | [2483065235C4](<Digital/ASUS/AUS24CA/2483065235C4>) |
| ASUS             | AUS24CA | VP247            | 1920x1080 | 23.4 | 2019 | [010A4192B938](<Digital/ASUS/AUS24CA/010A4192B938>) |
| ASUS             | AUS24CA | VP247            | 1920x1080 | 23.4 | 2018 | [0101E0ABFCD3](<Digital/ASUS/AUS24CA/0101E0ABFCD3>) |
| ASUS             | AUS24CA | VP247            | 1920x1080 | 23.4 | 2017 | [3ADE2945B89C](<Digital/ASUS/AUS24CA/3ADE2945B89C>) |
| ASUS             | AUS24CA |                  | 1920x1080 | 23.4 |      | [A555C69B65A6](<Digital/ASUS/AUS24CA/A555C69B65A6>) |
| ASUS             | AUS24CB | VP248            | 1920x1080 | 24.0 | 2020 | [36AB8A4C0C3A](<Digital/ASUS/AUS24CB/36AB8A4C0C3A>) |
| ASUS             | AUS24CB | VP248            | 1920x1080 | 24.0 | 2019 | [06AD2183913A](<Digital/ASUS/AUS24CB/06AD2183913A>) |
| ASUS             | AUS24CB | VP248            | 1920x1080 | 24.0 | 2018 | [49893E386D8B](<Digital/ASUS/AUS24CB/49893E386D8B>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2023 | [A5F89671B14A](<Digital/ASUS/AUS24CC/A5F89671B14A>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2021 | [086F3DBA9441](<Digital/ASUS/AUS24CC/086F3DBA9441>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2020 | [1B1D876A22C1](<Digital/ASUS/AUS24CC/1B1D876A22C1>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2019 | [01D8164A1D9A](<Digital/ASUS/AUS24CC/01D8164A1D9A>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2018 | [21EF2B150778](<Digital/ASUS/AUS24CC/21EF2B150778>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2017 | [2B8B376A72F4](<Digital/ASUS/AUS24CC/2B8B376A72F4>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2016 | [EDD7D3921E91](<Digital/ASUS/AUS24CC/EDD7D3921E91>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 | 2012 | [747978148BF5](<Digital/ASUS/AUS24CC/747978148BF5>) |
| ASUS             | AUS24CC | VZ249            | 1920x1080 | 24.0 |      | [107BD37E10FE](<Digital/ASUS/AUS24CC/107BD37E10FE>) |
| ASUS             | AUS24D0 | VY249HF          | 1920x1080 | 24.0 | 2024 | [1EB0B27B0C3D](<Digital/ASUS/AUS24D0/1EB0B27B0C3D>) |
| ASUS             | AUS24D0 | VY249HF          | 1920x1080 | 24.0 | 2023 | [98885BAEC854](<Digital/ASUS/AUS24D0/98885BAEC854>) |
| ASUS             | AUS24D1 | VA24E            | 1920x1080 | 24.0 | 2024 | [DA754131B7D3](<Digital/ASUS/AUS24D1/DA754131B7D3>) |
| ASUS             | AUS24D1 | VA24E            | 1920x1080 | 24.0 | 2023 | [0B2336F6DFFC](<Digital/ASUS/AUS24D1/0B2336F6DFFC>) |
| ASUS             | AUS24D1 | VA24E            | 1920x1080 | 24.0 | 2022 | [17F7DFA9D379](<Digital/ASUS/AUS24D1/17F7DFA9D379>) |
| ASUS             | AUS24D1 | VA24E            | 1920x1080 | 24.0 | 2021 | [0573DA42D5C6](<Digital/ASUS/AUS24D1/0573DA42D5C6>) |
| ASUS             | AUS24D1 | VA24E            | 1920x1080 | 24.0 | 2020 | [020A0B53CE93](<Digital/ASUS/AUS24D1/020A0B53CE93>) |
| ASUS             | AUS24D1 | VA24E            | 1920x1080 | 24.0 | 2019 | [23336B577916](<Digital/ASUS/AUS24D1/23336B577916>) |
| ASUS             | AUS24D1 |                  | 1920x1080 | 24.0 |      | [2022131E6847](<Digital/ASUS/AUS24D1/2022131E6847>) |
| ASUS             | AUS24D2 | VA247            | 1920x1080 | 24.0 | 2023 | [171D3B119D10](<Digital/ASUS/AUS24D2/171D3B119D10>) |
| ASUS             | AUS24D2 | VA247            | 1920x1080 | 24.0 | 2022 | [0B5BEE58466D](<Digital/ASUS/AUS24D2/0B5BEE58466D>) |
| ASUS             | AUS24D2 | VA247            | 1920x1080 | 24.0 | 2021 | [2A6CEE0D0D19](<Digital/ASUS/AUS24D2/2A6CEE0D0D19>) |
| ASUS             | AUS24D4 | VZ24EHE          | 1920x1080 | 24.0 | 2023 | [392FFD41197E](<Digital/ASUS/AUS24D4/392FFD41197E>) |
| ASUS             | AUS24D4 | VZ24EHE          | 1920x1080 | 24.0 | 2022 | [057B145C8ADF](<Digital/ASUS/AUS24D4/057B145C8ADF>) |
| ASUS             | AUS24D4 | VZ24EHE          | 1920x1080 | 24.0 | 2021 | [E529E9C73946](<Digital/ASUS/AUS24D4/E529E9C73946>) |
| ASUS             | AUS24D8 | VY249HGR         | 1920x1080 | 24.0 | 2024 | [67E58A3996BC](<Digital/ASUS/AUS24D8/67E58A3996BC>) |
| ASUS             | AUS24DA | VP247            | 1920x1080 | 23.4 | 2021 | [95DC3BDE7743](<Digital/ASUS/AUS24DA/95DC3BDE7743>) |
| ASUS             | AUS24DA | VP247            | 1920x1080 | 23.4 | 2020 | [2171117BBF63](<Digital/ASUS/AUS24DA/2171117BBF63>) |
| ASUS             | AUS24DA | VP247            | 1920x1080 | 23.4 | 2019 | [0F7B9C84E1A2](<Digital/ASUS/AUS24DA/0F7B9C84E1A2>) |
| ASUS             | AUS24DA | VP247            | 1920x1080 | 23.4 | 2018 | [1AE3CD98A9DC](<Digital/ASUS/AUS24DA/1AE3CD98A9DC>) |
| ASUS             | AUS24DA |                  | 1920x1080 | 23.4 |      | [84AB0D15CFB6](<Digital/ASUS/AUS24DA/84AB0D15CFB6>) |
| ASUS             | AUS24DB | VY249            | 1920x1080 | 24.0 | 2023 | [30150FE86A1F](<Digital/ASUS/AUS24DB/30150FE86A1F>) |
| ASUS             | AUS24DB | VY249            | 1920x1080 | 24.0 | 2022 | [20805CCDAE82](<Digital/ASUS/AUS24DB/20805CCDAE82>) |
| ASUS             | AUS24DB | VY249            | 1920x1080 | 24.0 | 2021 | [3514D193C42D](<Digital/ASUS/AUS24DB/3514D193C42D>) |
| ASUS             | AUS24DB | VY249            | 1920x1080 | 24.0 | 2020 | [5E1B4EE751FF](<Digital/ASUS/AUS24DB/5E1B4EE751FF>) |
| ASUS             | AUS24DC | VY249HGE         | 1920x1080 | 24.0 | 2024 | [433EAEFD4291](<Digital/ASUS/AUS24DC/433EAEFD4291>) |
| ASUS             | AUS24DC | VY249HGE         | 1920x1080 | 24.0 | 2023 | [4AAC91E4277E](<Digital/ASUS/AUS24DC/4AAC91E4277E>) |
| ASUS             | AUS24DD | VZ24EHF          | 1920x1080 | 24.0 | 2024 | [172A12E20F86](<Digital/ASUS/AUS24DD/172A12E20F86>) |
| ASUS             | AUS24DE | VA249HG          | 1920x1080 | 24.0 | 2024 | [54D4B1C228FF](<Digital/ASUS/AUS24DE/54D4B1C228FF>) |
| ASUS             | AUS24E3 | VA249QG          | 1920x1080 | 24.0 | 2024 | [5CD6177DC77B](<Digital/ASUS/AUS24E3/5CD6177DC77B>) |
| ASUS             | AUS24EE | PA248CRV         | 1920x1200 | 24.0 | 2023 | [BDB815F93B84](<Digital/ASUS/AUS24EE/BDB815F93B84>) |
| ASUS             | AUS2581 | VG258QM          | 1920x1080 | 24.3 | 2023 | [43653C6EAE12](<Digital/ASUS/AUS2581/43653C6EAE12>) |
| ASUS             | AUS2581 | VG258QM          | 1920x1080 | 24.3 | 2021 | [40589BADF063](<Digital/ASUS/AUS2581/40589BADF063>) |
| ASUS             | AUS2581 | VG258QM          | 1920x1080 | 24.3 | 2020 | [2FDE88666276](<Digital/ASUS/AUS2581/2FDE88666276>) |
| ASUS             | AUS2582 | VG258QM          | 1920x1080 | 24.3 | 2021 | [0ECF9199ABDF](<Digital/ASUS/AUS2582/0ECF9199ABDF>) |
| ASUS             | AUS2589 | VG259Q3A         | 1920x1080 | 24.3 | 2024 | [44B7BFA97BBB](<Digital/ASUS/AUS2589/44B7BFA97BBB>) |
| ASUS             | AUS258A | VG259Q5A         | 1920x1080 | 24.3 | 2025 | [1ED980270959](<Digital/ASUS/AUS258A/1ED980270959>) |
| ASUS             | AUS25A1 | VG255            | 1920x1080 | 24.3 | 2019 | [4C8F32739CDC](<Digital/ASUS/AUS25A1/4C8F32739CDC>) |
| ASUS             | AUS25A1 | VG255            | 1920x1080 | 24.3 | 2018 | [F413B39FF307](<Digital/ASUS/AUS25A1/F413B39FF307>) |
| ASUS             | AUS25A1 | VG255            | 1920x1080 | 24.3 | 2017 | [ECD792947C43](<Digital/ASUS/AUS25A1/ECD792947C43>) |
| ASUS             | AUS25A2 | VG258            | 1920x1080 | 24.3 | 2019 | [106F9FB44A4F](<Digital/ASUS/AUS25A2/106F9FB44A4F>) |
| ASUS             | AUS25A3 | VG258            | 1920x1080 | 24.3 | 2021 | [2C82322B035C](<Digital/ASUS/AUS25A3/2C82322B035C>) |
| ASUS             | AUS25A3 | VG258            | 1920x1080 | 24.3 | 2020 | [455255F0F535](<Digital/ASUS/AUS25A3/455255F0F535>) |
| ASUS             | AUS25A3 | VG258            | 1920x1080 | 24.3 | 2019 | [2580BCFE9D4B](<Digital/ASUS/AUS25A3/2580BCFE9D4B>) |
| ASUS             | AUS25A4 | VG258            | 1920x1080 | 24.3 | 2021 | [0A3D75AB9D5C](<Digital/ASUS/AUS25A4/0A3D75AB9D5C>) |
| ASUS             | AUS25A4 | VG258            | 1920x1080 | 24.3 | 2020 | [68634D5DBBF0](<Digital/ASUS/AUS25A4/68634D5DBBF0>) |
| ASUS             | AUS25A4 | VG258            | 1920x1080 | 24.3 | 2019 | [FDFD4E64672E](<Digital/ASUS/AUS25A4/FDFD4E64672E>) |
| ASUS             | AUS25A4 | VG258            | 1920x1080 | 24.3 | 2018 | [BB1C66824C47](<Digital/ASUS/AUS25A4/BB1C66824C47>) |
| ASUS             | AUS25A4 | VG258            | 1920x1080 | 24.3 |      | [73440D667524](<Digital/ASUS/AUS25A4/73440D667524>) |
| ASUS             | AUS25A5 | VG259            | 1920x1080 | 24.3 | 2021 | [7CA170F2DE09](<Digital/ASUS/AUS25A5/7CA170F2DE09>) |
| ASUS             | AUS25A5 | VG259            | 1920x1080 | 24.3 | 2020 | [67D0539DD4EE](<Digital/ASUS/AUS25A5/67D0539DD4EE>) |
| ASUS             | AUS25A5 | VG259            | 1920x1080 | 24.3 | 2019 | [7BA9462BE41C](<Digital/ASUS/AUS25A5/7BA9462BE41C>) |
| ASUS             | AUS25A6 | VG259            | 1920x1080 | 24.3 | 2022 | [272489A89DC4](<Digital/ASUS/AUS25A6/272489A89DC4>) |
| ASUS             | AUS25A6 | VG259            | 1920x1080 | 24.3 | 2021 | [A375F0345123](<Digital/ASUS/AUS25A6/A375F0345123>) |
| ASUS             | AUS25A6 | VG259            | 1920x1080 | 24.3 | 2020 | [0B6F2B9247FD](<Digital/ASUS/AUS25A6/0B6F2B9247FD>) |
| ASUS             | AUS25A6 | VG259            | 1920x1080 | 24.3 | 2019 | [7F68C01C34BB](<Digital/ASUS/AUS25A6/7F68C01C34BB>) |
| ASUS             | AUS25A8 | VG259QM          | 1920x1080 | 24.3 | 2021 | [A5F1CE3B5E82](<Digital/ASUS/AUS25A8/A5F1CE3B5E82>) |
| ASUS             | AUS25A8 | VG259QM          | 1920x1080 | 24.3 | 2020 | [5055C7591445](<Digital/ASUS/AUS25A8/5055C7591445>) |
| ASUS             | AUS25A9 | VG259QM          | 1920x1080 | 24.3 | 2023 | [2AF3D23315F4](<Digital/ASUS/AUS25A9/2AF3D23315F4>) |
| ASUS             | AUS25A9 | VG259QM          | 1920x1080 | 24.3 | 2021 | [0290E5DCE5F4](<Digital/ASUS/AUS25A9/0290E5DCE5F4>) |
| ASUS             | AUS25A9 | VG259QM          | 1920x1080 | 24.3 | 2020 | [0941BFA15412](<Digital/ASUS/AUS25A9/0941BFA15412>) |
| ASUS             | AUS25AB | VG259QR          | 1920x1080 | 24.3 | 2023 | [08E9D1649C98](<Digital/ASUS/AUS25AB/08E9D1649C98>) |
| ASUS             | AUS25AB | VG259QR          | 1920x1080 | 24.3 | 2021 | [21024C3ED281](<Digital/ASUS/AUS25AB/21024C3ED281>) |
| ASUS             | AUS25AB | VG259QR          | 1920x1080 | 24.3 | 2020 | [78D02BCC0C24](<Digital/ASUS/AUS25AB/78D02BCC0C24>) |
| ASUS             | AUS25AC | VG259QR          | 1920x1080 | 24.3 | 2022 | [6A4119E0DEA2](<Digital/ASUS/AUS25AC/6A4119E0DEA2>) |
| ASUS             | AUS25AC | VG259QR          | 1920x1080 | 24.3 | 2021 | [59BFE8EEF724](<Digital/ASUS/AUS25AC/59BFE8EEF724>) |
| ASUS             | AUS25B1 | ROG PG258Q       | 1920x1080 | 24.3 | 2019 | [19E6267F1F97](<Digital/ASUS/AUS25B1/19E6267F1F97>) |
| ASUS             | AUS25B1 | ROG PG258Q       | 1920x1080 | 24.3 | 2018 | [1A13E97CA763](<Digital/ASUS/AUS25B1/1A13E97CA763>) |
| ASUS             | AUS25B1 | ROG PG258Q       | 1920x1080 | 24.3 | 2017 | [43AB8BEB6F52](<Digital/ASUS/AUS25B1/43AB8BEB6F52>) |
| ASUS             | AUS25B3 | XG258            | 1920x1080 | 24.3 | 2020 | [E6482BA4B8A6](<Digital/ASUS/AUS25B3/E6482BA4B8A6>) |
| ASUS             | AUS25B3 | XG258            | 1920x1080 | 24.3 | 2019 | [81F00E6523FF](<Digital/ASUS/AUS25B3/81F00E6523FF>) |
| ASUS             | AUS25B3 | XG258            | 1920x1080 | 24.3 | 2018 | [628AF43F52B0](<Digital/ASUS/AUS25B3/628AF43F52B0>) |
| ASUS             | AUS25B3 | XG258            | 1920x1080 | 24.3 | 2017 | [36B0F1C8F32A](<Digital/ASUS/AUS25B3/36B0F1C8F32A>) |
| ASUS             | AUS25B4 | ROG PG259QN      | 1920x1080 | 24.3 | 2021 | [DBF8E1441E36](<Digital/ASUS/AUS25B4/DBF8E1441E36>) |
| ASUS             | AUS25B5 | ROG PG259QN      | 1920x1080 | 24.3 | 2022 | [EDDC74154A52](<Digital/ASUS/AUS25B5/EDDC74154A52>) |
| ASUS             | AUS25B5 | ROG PG259QN      | 1920x1080 | 24.3 | 2021 | [1D0B109A50E2](<Digital/ASUS/AUS25B5/1D0B109A50E2>) |
| ASUS             | AUS25B5 | ROG PG259QN      | 1920x1080 | 24.3 | 2020 | [82D0EB4F22C3](<Digital/ASUS/AUS25B5/82D0EB4F22C3>) |
| ASUS             | AUS25B6 | ROG PG259QNR     | 1920x1080 | 24.3 | 2021 | [6AA2F0F43530](<Digital/ASUS/AUS25B6/6AA2F0F43530>) |
| ASUS             | AUS25B7 | ROG PG259QNR     | 1920x1080 | 24.3 | 2021 | [38741A4182B7](<Digital/ASUS/AUS25B7/38741A4182B7>) |
| ASUS             | AUS25B9 | XG256Q           | 1920x1080 | 24.3 | 2022 | [9A9C697604DB](<Digital/ASUS/AUS25B9/9A9C697604DB>) |
| ASUS             | AUS25BC | XG259CS          | 1920x1080 | 24.3 | 2024 | [1FE51284A1A2](<Digital/ASUS/AUS25BC/1FE51284A1A2>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 | 2025 | [5ADB223BFEC9](<Digital/ASUS/AUS2700/5ADB223BFEC9>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 | 2024 | [324A2067CBD7](<Digital/ASUS/AUS2700/324A2067CBD7>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 | 2023 | [094BF2FDB378](<Digital/ASUS/AUS2700/094BF2FDB378>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 | 2022 | [3F3033216679](<Digital/ASUS/AUS2700/3F3033216679>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 | 2021 | [06A56C1AD439](<Digital/ASUS/AUS2700/06A56C1AD439>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 | 2020 | [284B19DA6BB9](<Digital/ASUS/AUS2700/284B19DA6BB9>) |
| ASUS             | AUS2700 | PA278QV          | 2560x1440 | 27.2 |      | [35543F8B17A7](<Digital/ASUS/AUS2700/35543F8B17A7>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 | 2025 | [A87CB7940DC1](<Digital/ASUS/AUS2701/A87CB7940DC1>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 | 2024 | [9ADE50B01047](<Digital/ASUS/AUS2701/9ADE50B01047>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 | 2023 | [1ECFF78CF739](<Digital/ASUS/AUS2701/1ECFF78CF739>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 | 2022 | [076389353058](<Digital/ASUS/AUS2701/076389353058>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 | 2021 | [0F49AEC856BD](<Digital/ASUS/AUS2701/0F49AEC856BD>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 | 2020 | [078F72CCAD7A](<Digital/ASUS/AUS2701/078F72CCAD7A>) |
| ASUS             | AUS2701 | PA278QV          | 2560x1440 | 27.2 |      | [9C1903C5587B](<Digital/ASUS/AUS2701/9C1903C5587B>) |
| ASUS             | AUS2702 | VG279QL1A        | 1920x1080 | 27.2 | 2021 | [1CC2FE135697](<Digital/ASUS/AUS2702/1CC2FE135697>) |
| ASUS             | AUS2702 | VG279QL1A        | 1920x1080 | 27.2 |      | [DF4AC72F2636](<Digital/ASUS/AUS2702/DF4AC72F2636>) |
| ASUS             | AUS2703 | VG279Q1A         | 1920x1080 | 27.2 | 2023 | [542507EBE72C](<Digital/ASUS/AUS2703/542507EBE72C>) |
| ASUS             | AUS2703 | PA278QV          | 2560x1440 | 27.2 | 2022 | [9A23186126A4](<Digital/ASUS/AUS2703/9A23186126A4>) |
| ASUS             | AUS2703 |                  | 1920x1080 | 27.2 | 2021 | [B4AE2B175BC5](<Digital/ASUS/AUS2703/B4AE2B175BC5>) |
| ASUS             | AUS2703 |                  | 1920x1080 | 27.2 | 2020 | [0326F0139196](<Digital/ASUS/AUS2703/0326F0139196>) |
| ASUS             | AUS2704 | VG27AQL1A        | 2560x1440 | 27.2 | 2024 | [3CDA6EC5145A](<Digital/ASUS/AUS2704/3CDA6EC5145A>) |
| ASUS             | AUS2704 | VG27AQL1A        | 2560x1440 | 27.2 | 2023 | [59FAEE1BBCC1](<Digital/ASUS/AUS2704/59FAEE1BBCC1>) |
| ASUS             | AUS2704 | VG27AQL1A        | 2560x1440 | 27.2 | 2021 | [08871F7D1214](<Digital/ASUS/AUS2704/08871F7D1214>) |
| ASUS             | AUS2704 | VG27AQL1A        | 3840x2160 | 27.2 | 2021 | [E355B3755A6B](<Digital/ASUS/AUS2704/E355B3755A6B>) |
| ASUS             | AUS2704 | VG27AQL1A        | 2560x1440 | 27.2 | 2020 | [2412FCD4D453](<Digital/ASUS/AUS2704/2412FCD4D453>) |
| ASUS             | AUS2704 | VG27AQL1A        | 2560x1440 | 27.2 |      | [61F72573E738](<Digital/ASUS/AUS2704/61F72573E738>) |
| ASUS             | AUS2705 | VG27AQL1A        | 2560x1440 | 27.2 | 2023 | [177F1EACBD00](<Digital/ASUS/AUS2705/177F1EACBD00>) |
| ASUS             | AUS2705 | VG27AQL1A        | 2560x1440 | 27.2 | 2022 | [10F0520AF3D3](<Digital/ASUS/AUS2705/10F0520AF3D3>) |
| ASUS             | AUS2705 | VG27AQL1A        | 2560x1440 | 27.2 | 2021 | [0C06B69DB62D](<Digital/ASUS/AUS2705/0C06B69DB62D>) |
| ASUS             | AUS2705 | VG27AQL1A        | 2560x1440 | 27.2 | 2020 | [053E371E2F53](<Digital/ASUS/AUS2705/053E371E2F53>) |
| ASUS             | AUS2706 | VG27AQ1A         | 2560x1440 | 27.2 | 2024 | [924534C8ACEF](<Digital/ASUS/AUS2706/924534C8ACEF>) |
| ASUS             | AUS2706 | VG27AQ1A         | 2560x1440 | 27.2 | 2023 | [0C78799B1A89](<Digital/ASUS/AUS2706/0C78799B1A89>) |
| ASUS             | AUS2706 | VG27AQ1A         | 2560x1440 | 27.2 | 2022 | [055D65A16A37](<Digital/ASUS/AUS2706/055D65A16A37>) |
| ASUS             | AUS2706 | VG27AQ1A         | 2560x1440 | 27.2 | 2021 | [2A9098D9560A](<Digital/ASUS/AUS2706/2A9098D9560A>) |
| ASUS             | AUS2706 | VG27AQ1A         | 2560x1440 | 27.2 | 2020 | [2E32669B0BEC](<Digital/ASUS/AUS2706/2E32669B0BEC>) |
| ASUS             | AUS2707 | VG27AQ1A         | 2560x1440 | 27.2 | 2024 | [491D1D7007CC](<Digital/ASUS/AUS2707/491D1D7007CC>) |
| ASUS             | AUS2707 | VG27AQ1A         | 2560x1440 | 27.2 | 2023 | [0E0D0030B4BD](<Digital/ASUS/AUS2707/0E0D0030B4BD>) |
| ASUS             | AUS2707 | VG27AQ1A         | 2560x1440 | 27.2 | 2022 | [16030347BDEA](<Digital/ASUS/AUS2707/16030347BDEA>) |
| ASUS             | AUS2707 | VG27AQ1A         | 2560x1440 | 27.2 | 2021 | [1D9BAB3C0CE8](<Digital/ASUS/AUS2707/1D9BAB3C0CE8>) |
| ASUS             | AUS2707 | VG27AQ1A         | 2560x1440 | 27.2 | 2020 | [236278C515B5](<Digital/ASUS/AUS2707/236278C515B5>) |
| ASUS             | AUS2708 | VG2791R          | 1920x1080 | 26.6 | 2023 | [1D0FACBA5C39](<Digital/ASUS/AUS2708/1D0FACBA5C39>) |
| ASUS             | AUS2708 | VG2791R          | 1920x1080 | 26.6 | 2021 | [0286E1E85EA5](<Digital/ASUS/AUS2708/0286E1E85EA5>) |
| ASUS             | AUS2708 | VG2791R          | 1920x1080 | 26.6 | 2020 | [2207D5A1FC86](<Digital/ASUS/AUS2708/2207D5A1FC86>) |
| ASUS             | AUS2709 | ROG PG279QM      | 2560x1440 | 27.2 | 2022 | [DD10E696E67D](<Digital/ASUS/AUS2709/DD10E696E67D>) |
| ASUS             | AUS270A | VA27D            | 1920x1080 | 27.2 | 2023 | [A2F3DFAB224B](<Digital/ASUS/AUS270A/A2F3DFAB224B>) |
| ASUS             | AUS270A | VA27D            | 1920x1080 | 27.2 | 2022 | [0764613BA2D4](<Digital/ASUS/AUS270A/0764613BA2D4>) |
| ASUS             | AUS270A | VA27D            | 1920x1080 | 27.2 | 2021 | [5B400E6CBD7B](<Digital/ASUS/AUS270A/5B400E6CBD7B>) |
| ASUS             | AUS270A | VA27D            | 1920x1080 | 27.2 | 2020 | [1C1914EDDF1A](<Digital/ASUS/AUS270A/1C1914EDDF1A>) |
| ASUS             | AUS270B | VA27D            | 1920x1080 | 27.2 | 2023 | [6398B45DFDAE](<Digital/ASUS/AUS270B/6398B45DFDAE>) |
| ASUS             | AUS270B | VA27D            | 1920x1080 | 27.2 | 2021 | [476C70C67C4F](<Digital/ASUS/AUS270B/476C70C67C4F>) |
| ASUS             | AUS270B | VA27D            | 1920x1080 | 27.2 | 2020 | [33DE63A54D10](<Digital/ASUS/AUS270B/33DE63A54D10>) |
| ASUS             | AUS270C | VA27A            | 2560x1440 | 27.2 | 2022 | [4828AFAFEA80](<Digital/ASUS/AUS270C/4828AFAFEA80>) |
| ASUS             | AUS270C | VA27A            | 2560x1440 | 27.2 | 2021 | [21E286FEF3D1](<Digital/ASUS/AUS270C/21E286FEF3D1>) |
| ASUS             | AUS270C | VA27A            | 2560x1440 | 27.2 | 2020 | [CFC1E6EB7CB9](<Digital/ASUS/AUS270C/CFC1E6EB7CB9>) |
| ASUS             | AUS270E | VG279QR          | 1920x1080 | 27.2 | 2023 | [D29D18A6F267](<Digital/ASUS/AUS270E/D29D18A6F267>) |
| ASUS             | AUS270E | VG279QR          | 1920x1080 | 27.2 | 2021 | [06B7A5DFC6A8](<Digital/ASUS/AUS270E/06B7A5DFC6A8>) |
| ASUS             | AUS270F | VG279QR          | 1920x1080 | 27.2 | 2023 | [9A686915BFC1](<Digital/ASUS/AUS270F/9A686915BFC1>) |
| ASUS             | AUS270F | VG279QR          | 1920x1080 | 27.2 | 2021 | [10B705403C57](<Digital/ASUS/AUS270F/10B705403C57>) |
| ASUS             | AUS2712 | ROG XG27AQM      | 2560x1440 | 27.2 | 2021 | [AB16873CA407](<Digital/ASUS/AUS2712/AB16873CA407>) |
| ASUS             | AUS2713 | VA279QG          | 1920x1080 | 27.2 | 2024 | [282F3E354234](<Digital/ASUS/AUS2713/282F3E354234>) |
| ASUS             | AUS2714 | VA279HG          | 1920x1080 | 27.2 | 2025 | [A311F3100F05](<Digital/ASUS/AUS2714/A311F3100F05>) |
| ASUS             | AUS2718 | VG27AQ5A         | 2560x1440 | 27.2 | 2025 | [B37267E0719B](<Digital/ASUS/AUS2718/B37267E0719B>) |
| ASUS             | AUS2719 | VG27AQL5A        | 2560x1440 | 27.2 | 2025 | [0CDAA561B9EF](<Digital/ASUS/AUS2719/0CDAA561B9EF>) |
| ASUS             | AUS271A | VA27ACFSN        | 2560x1440 | 27.2 | 2024 | [967A19E1E69B](<Digital/ASUS/AUS271A/967A19E1E69B>) |
| ASUS             | AUS271C | XG27ACMS         | 2560x1440 | 27.2 | 2024 | [CC381FAA7D1A](<Digital/ASUS/AUS271C/CC381FAA7D1A>) |
| ASUS             | AUS271F | MS27UC           | 3840x2160 | 27.2 | 2024 | [BF0C8E2358BB](<Digital/ASUS/AUS271F/BF0C8E2358BB>) |
| ASUS             | AUS2720 | VG278            | 1920x1080 | 27.2 | 2023 | [AB4DBFBB536B](<Digital/ASUS/AUS2720/AB4DBFBB536B>) |
| ASUS             | AUS2720 | VG278            | 1920x1080 | 27.2 | 2021 | [22539CD939CC](<Digital/ASUS/AUS2720/22539CD939CC>) |
| ASUS             | AUS2720 | VG278            | 1920x1080 | 27.2 | 2020 | [1921015D2FBA](<Digital/ASUS/AUS2720/1921015D2FBA>) |
| ASUS             | AUS2720 | VG278            | 1920x1080 | 27.2 | 2019 | [1C4E98E2E49B](<Digital/ASUS/AUS2720/1C4E98E2E49B>) |
| ASUS             | AUS2720 | VG278            | 1920x1080 | 27.2 | 2018 | [D0C025FE0855](<Digital/ASUS/AUS2720/D0C025FE0855>) |
| ASUS             | AUS2721 | VG279QM          | 1920x1080 | 27.2 | 2024 | [88E8054EDE7C](<Digital/ASUS/AUS2721/88E8054EDE7C>) |
| ASUS             | AUS2721 | VG279QM          | 1920x1080 | 27.2 | 2023 | [7E21C077D513](<Digital/ASUS/AUS2721/7E21C077D513>) |
| ASUS             | AUS2721 | VG279QM          | 1920x1080 | 27.2 | 2021 | [02259E9A414D](<Digital/ASUS/AUS2721/02259E9A414D>) |
| ASUS             | AUS2721 | VG279QM          | 1920x1080 | 27.2 | 2020 | [0A659791CBCF](<Digital/ASUS/AUS2721/0A659791CBCF>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 | 2024 | [0FFAF52EFAE2](<Digital/ASUS/AUS2722/0FFAF52EFAE2>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 | 2023 | [032348D8877A](<Digital/ASUS/AUS2722/032348D8877A>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 | 2022 | [06D446DE3E20](<Digital/ASUS/AUS2722/06D446DE3E20>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 | 2021 | [01FC13E898A6](<Digital/ASUS/AUS2722/01FC13E898A6>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 | 2020 | [003EA06D16FA](<Digital/ASUS/AUS2722/003EA06D16FA>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 | 2019 | [098F50008E76](<Digital/ASUS/AUS2722/098F50008E76>) |
| ASUS             | AUS2722 | VG27A            | 2560x1440 | 27.2 |      | [3726963C01FA](<Digital/ASUS/AUS2722/3726963C01FA>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2024 | [12ECF300EC55](<Digital/ASUS/AUS2723/12ECF300EC55>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2023 | [0E33B3A0C422](<Digital/ASUS/AUS2723/0E33B3A0C422>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2022 | [0A777BD8DD39](<Digital/ASUS/AUS2723/0A777BD8DD39>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2021 | [14063FB2EE74](<Digital/ASUS/AUS2723/14063FB2EE74>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2020 | [1571E0D417DE](<Digital/ASUS/AUS2723/1571E0D417DE>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2019 | [69CA53AD35EF](<Digital/ASUS/AUS2723/69CA53AD35EF>) |
| ASUS             | AUS2723 | VG27A            | 2560x1440 | 27.2 | 2018 | [4C758929FDDC](<Digital/ASUS/AUS2723/4C758929FDDC>) |
| ASUS             | AUS2724 | XG27WQ           | 2560x1440 | 27.7 | 2021 | [4AC2BE42194A](<Digital/ASUS/AUS2724/4AC2BE42194A>) |
| ASUS             | AUS2724 | XG27WQ           | 2560x1440 | 27.7 | 2020 | [18603844949C](<Digital/ASUS/AUS2724/18603844949C>) |
| ASUS             | AUS2725 | VG279Q1A         | 1920x1080 | 27.2 | 2021 | [063260A3F20D](<Digital/ASUS/AUS2725/063260A3F20D>) |
| ASUS             | AUS2725 | VG279Q1A         | 1920x1080 | 27.2 | 2020 | [518E88B4EBE2](<Digital/ASUS/AUS2725/518E88B4EBE2>) |
| ASUS             | AUS2726 | BE279QSK         | 1920x1080 | 27.2 | 2024 | [01889E979D70](<Digital/ASUS/AUS2726/01889E979D70>) |
| ASUS             | AUS272A | ROG XG27UQ       | 3840x2160 | 27.2 | 2020 | [2BCC3329AAD0](<Digital/ASUS/AUS272A/2BCC3329AAD0>) |
| ASUS             | AUS272A | ROG XG27UQ       | 3840x2160 | 27.2 | 2019 | [5480D7E90295](<Digital/ASUS/AUS272A/5480D7E90295>) |
| ASUS             | AUS272A | ROG              | 3840x2160 | 27.2 |      | [DFBAE737BE84](<Digital/ASUS/AUS272A/DFBAE737BE84>) |
| ASUS             | AUS272B | VG27WQ           | 2560x1440 | 27.2 | 2024 | [6B347A9FD93F](<Digital/ASUS/AUS272B/6B347A9FD93F>) |
| ASUS             | AUS272B | VG27WQ           | 2560x1440 | 27.2 | 2023 | [019C61D60315](<Digital/ASUS/AUS272B/019C61D60315>) |
| ASUS             | AUS272B | VG27WQ           | 2560x1440 | 27.2 | 2021 | [190684DA36AD](<Digital/ASUS/AUS272B/190684DA36AD>) |
| ASUS             | AUS272B | VG27WQ           | 2560x1440 | 27.2 | 2020 | [20B7CAD24F1E](<Digital/ASUS/AUS272B/20B7CAD24F1E>) |
| ASUS             | AUS272B | VG27WQ           | 2560x1440 | 27.2 | 2019 | [5FB562110AA0](<Digital/ASUS/AUS272B/5FB562110AA0>) |
| ASUS             | AUS272B | VG27WQ           | 2560x1440 | 27.2 |      | [4E2CC46ABE3E](<Digital/ASUS/AUS272B/4E2CC46ABE3E>) |
| ASUS             | AUS272D | VG277Q1A         | 1920x1080 | 27.2 | 2024 | [195D15623070](<Digital/ASUS/AUS272D/195D15623070>) |
| ASUS             | AUS272D | VG277Q1A         | 1920x1080 | 27.2 | 2023 | [103163FB333D](<Digital/ASUS/AUS272D/103163FB333D>) |
| ASUS             | AUS272D | VG277Q1A         | 1920x1080 | 27.2 | 2022 | [02AF33124539](<Digital/ASUS/AUS272D/02AF33124539>) |
| ASUS             | AUS272D | VG277Q1A         | 1920x1080 | 27.2 | 2021 | [EB8971726C75](<Digital/ASUS/AUS272D/EB8971726C75>) |
| ASUS             | AUS272F | ROG PG279QM      | 2560x1440 | 27.2 | 2023 | [756709D27AF4](<Digital/ASUS/AUS272F/756709D27AF4>) |
| ASUS             | AUS272F | ROG PG279QM      | 2560x1440 | 27.2 | 2022 | [12E9DB1C4BB3](<Digital/ASUS/AUS272F/12E9DB1C4BB3>) |
| ASUS             | AUS2741 | XG27AQMR         | 2560x1440 | 27.2 | 2023 | [3B7C71EA3EC5](<Digital/ASUS/AUS2741/3B7C71EA3EC5>) |
| ASUS             | AUS2741 | XG27AQMR         | 2560x1440 | 27.2 | 2022 | [7CFD660A51B4](<Digital/ASUS/AUS2741/7CFD660A51B4>) |
| ASUS             | AUS2743 | VU279CFE         | 1920x1080 | 27.2 | 2024 | [8BE537C0CB28](<Digital/ASUS/AUS2743/8BE537C0CB28>) |
| ASUS             | AUS2744 | VA27DQF          | 1920x1080 | 27.2 | 2024 | [35AB3DEBE6E7](<Digital/ASUS/AUS2744/35AB3DEBE6E7>) |
| ASUS             | AUS2745 | VA27EHF          | 1920x1080 | 27.2 | 2022 | [0D559C1D882F](<Digital/ASUS/AUS2745/0D559C1D882F>) |
| ASUS             | AUS274B | PG27UQR          | 3840x2160 | 27.2 | 2023 | [01BEE4D4ECC8](<Digital/ASUS/AUS274B/01BEE4D4ECC8>) |
| ASUS             | AUS274C | XG27AQDPG        | 2560x1440 | 26.6 | 2025 | [765982A0FDA9](<Digital/ASUS/AUS274C/765982A0FDA9>) |
| ASUS             | AUS2751 | VG279QM1A        | 1920x1080 | 27.2 | 2023 | [DA734401DE7D](<Digital/ASUS/AUS2751/DA734401DE7D>) |
| ASUS             | AUS2752 | VG279Q3A         | 1920x1080 | 27.2 | 2022 | [01355CF7EB0A](<Digital/ASUS/AUS2752/01355CF7EB0A>) |
| ASUS             | AUS2753 | VG27AQM1A        | 2560x1440 | 27.2 | 2023 | [BF4D028FD2B2](<Digital/ASUS/AUS2753/BF4D028FD2B2>) |
| ASUS             | AUS2754 | XG27UCS          | 3840x2160 | 27.2 | 2023 | [389C0D417970](<Digital/ASUS/AUS2754/389C0D417970>) |
| ASUS             | AUS2755 | VG27UQ1A         | 3840x2160 | 27.2 | 2024 | [8BAD4437CABB](<Digital/ASUS/AUS2755/8BAD4437CABB>) |
| ASUS             | AUS2756 | VG27VQ3B         | 1920x1080 | 27.2 | 2023 | [45DFB771B9E1](<Digital/ASUS/AUS2756/45DFB771B9E1>) |
| ASUS             | AUS2757 | VG27VQM1B        | 1920x1080 | 27.2 | 2023 | [2E74C393EE58](<Digital/ASUS/AUS2757/2E74C393EE58>) |
| ASUS             | AUS275A | VG27AQ3A-L       | 2560x1440 | 27.2 | 2023 | [824D00FCEF80](<Digital/ASUS/AUS275A/824D00FCEF80>) |
| ASUS             | AUS275B | VG27AQL3A        | 2560x1440 | 27.2 | 2025 | [31A148F8253E](<Digital/ASUS/AUS275B/31A148F8253E>) |
| ASUS             | AUS275B | VG27AQL3A        | 2560x1440 | 27.2 | 2024 | [16D8574F5E47](<Digital/ASUS/AUS275B/16D8574F5E47>) |
| ASUS             | AUS275B | VG27AQL3A        | 2560x1440 | 27.2 | 2023 | [31A52E20B5E6](<Digital/ASUS/AUS275B/31A52E20B5E6>) |
| ASUS             | AUS275E | XG27WCMS         | 2560x1440 | 27.2 | 2024 | [B334B9270668](<Digital/ASUS/AUS275E/B334B9270668>) |
| ASUS             | AUS275F | XG27WCS          | 2560x1440 | 27.2 | 2025 | [043D82F4066D](<Digital/ASUS/AUS275F/043D82F4066D>) |
| ASUS             | AUS275F | XG27WCS          | 2560x1440 | 27.2 | 2024 | [0F207DA6454E](<Digital/ASUS/AUS275F/0F207DA6454E>) |
| ASUS             | AUS2761 | PA27UCGE         | 3840x2160 | 27.2 | 2025 | [5160CF9521B1](<Digital/ASUS/AUS2761/5160CF9521B1>) |
| ASUS             | AUS2762 | PA27A            | 2560x1440 | 27.2 | 2020 | [0F4470FB4AD8](<Digital/ASUS/AUS2762/0F4470FB4AD8>) |
| ASUS             | AUS2768 | PA279CV          | 3840x2160 | 27.2 | 2023 | [1D2CE7BF142C](<Digital/ASUS/AUS2768/1D2CE7BF142C>) |
| ASUS             | AUS2768 | PA279            | 3840x2160 | 27.2 | 2022 | [05DBC3FC382E](<Digital/ASUS/AUS2768/05DBC3FC382E>) |
| ASUS             | AUS2768 | PA279            | 3840x2160 | 27.2 | 2021 | [1ADCCEA9FCB6](<Digital/ASUS/AUS2768/1ADCCEA9FCB6>) |
| ASUS             | AUS2768 | PA279CV          | 3840x2160 | 27.2 | 2020 | [46A01EBA72FF](<Digital/ASUS/AUS2768/46A01EBA72FF>) |
| ASUS             | AUS276A | ROG XG27AQ       | 2560x1440 | 27.2 | 2023 | [9A714CEE5CFB](<Digital/ASUS/AUS276A/9A714CEE5CFB>) |
| ASUS             | AUS276A | ROG XG27AQ       | 2560x1440 | 27.2 | 2021 | [10BDDE606EB3](<Digital/ASUS/AUS276A/10BDDE606EB3>) |
| ASUS             | AUS276B | ROG XG27AQ       | 2560x1440 | 27.2 | 2023 | [4B918FF38483](<Digital/ASUS/AUS276B/4B918FF38483>) |
| ASUS             | AUS276B | ROG XG27AQ       | 2560x1440 | 27.2 | 2021 | [0A6BD269F7CB](<Digital/ASUS/AUS276B/0A6BD269F7CB>) |
| ASUS             | AUS276B | ROG XG27AQ       | 2560x1440 | 27.2 | 2020 | [4212E58EEC7E](<Digital/ASUS/AUS276B/4212E58EEC7E>) |
| ASUS             | AUS276C | PA278CV          | 2560x1440 | 27.2 | 2024 | [3978BED4AAA9](<Digital/ASUS/AUS276C/3978BED4AAA9>) |
| ASUS             | AUS276C | PA278CV          | 2560x1440 | 27.2 | 2023 | [0A18B573D0C6](<Digital/ASUS/AUS276C/0A18B573D0C6>) |
| ASUS             | AUS276C | PA278CV          | 2560x1440 | 27.2 | 2022 | [2667938B0407](<Digital/ASUS/AUS276C/2667938B0407>) |
| ASUS             | AUS276C | PA278CV          | 2560x1440 | 27.2 | 2021 | [83981AA37377](<Digital/ASUS/AUS276C/83981AA37377>) |
| ASUS             | AUS276D | PA278CV          | 2560x1440 | 27.2 | 2024 | [6B16B6162F1E](<Digital/ASUS/AUS276D/6B16B6162F1E>) |
| ASUS             | AUS276D | PA278CV          | 2560x1440 | 27.2 | 2023 | [00A5AD2BCA1C](<Digital/ASUS/AUS276D/00A5AD2BCA1C>) |
| ASUS             | AUS276D | PA278CV          | 2560x1440 | 27.2 | 2022 | [1F9287B87269](<Digital/ASUS/AUS276D/1F9287B87269>) |
| ASUS             | AUS276D | PA278CV          | 2560x1440 | 27.2 | 2021 | [06383D97A51F](<Digital/ASUS/AUS276D/06383D97A51F>) |
| ASUS             | AUS276E | BE27ACSBK        | 2560x1440 | 27.2 | 2021 | [58FE999E1AD3](<Digital/ASUS/AUS276E/58FE999E1AD3>) |
| ASUS             | AUS276F | PA278CFRV        | 2560x1440 | 27.2 | 2024 | [8086B5C3A0CF](<Digital/ASUS/AUS276F/8086B5C3A0CF>) |
| ASUS             | AUS2771 | PA27JCV          | 2560x1440 | 27.2 | 2025 | [36B09CC8445E](<Digital/ASUS/AUS2771/36B09CC8445E>) |
| ASUS             | AUS2780 | VG279            | 1920x1080 | 27.2 | 2021 | [7F2D99730886](<Digital/ASUS/AUS2780/7F2D99730886>) |
| ASUS             | AUS2780 | VG279            | 1920x1080 | 27.2 | 2020 | [04C486D50A8B](<Digital/ASUS/AUS2780/04C486D50A8B>) |
| ASUS             | AUS2780 | VG279            | 1920x1080 | 27.2 | 2019 | [0344129D8E1F](<Digital/ASUS/AUS2780/0344129D8E1F>) |
| ASUS             | AUS2780 | VG279            | 1920x1080 | 27.2 | 2018 | [275E1E71F952](<Digital/ASUS/AUS2780/275E1E71F952>) |
| ASUS             | AUS2781 | VL279            | 1920x1080 | 27.2 | 2021 | [1DEC2F2F3430](<Digital/ASUS/AUS2781/1DEC2F2F3430>) |
| ASUS             | AUS2781 | VL279            | 1920x1080 | 27.2 | 2020 | [0FC630DCCDE3](<Digital/ASUS/AUS2781/0FC630DCCDE3>) |
| ASUS             | AUS2782 | VG279            | 1920x1080 | 27.2 | 2021 | [1855FA6E6921](<Digital/ASUS/AUS2782/1855FA6E6921>) |
| ASUS             | AUS2782 | VG279            | 1920x1080 | 27.2 | 2020 | [0F51B9BBB558](<Digital/ASUS/AUS2782/0F51B9BBB558>) |
| ASUS             | AUS2782 | VG279            | 1920x1080 | 27.2 | 2019 | [0EC2125A51A6](<Digital/ASUS/AUS2782/0EC2125A51A6>) |
| ASUS             | AUS2782 | VG279            | 1920x1080 | 27.2 | 2018 | [54FFB4BBA2A3](<Digital/ASUS/AUS2782/54FFB4BBA2A3>) |
| ASUS             | AUS2782 | VG279            | 1920x1080 | 27.2 |      | [B09085B13377](<Digital/ASUS/AUS2782/B09085B13377>) |
| ASUS             | AUS2785 | VG27B            | 2560x1440 | 27.2 | 2022 | [F1708578AB13](<Digital/ASUS/AUS2785/F1708578AB13>) |
| ASUS             | AUS2785 | VG27B            | 2560x1440 | 27.2 | 2021 | [2A89A889A80E](<Digital/ASUS/AUS2785/2A89A889A80E>) |
| ASUS             | AUS2785 | VG27B            | 2560x1440 | 27.2 | 2020 | [319954E31662](<Digital/ASUS/AUS2785/319954E31662>) |
| ASUS             | AUS2785 | VG27B            | 2560x1440 | 27.2 | 2019 | [EFD3EC9DC84C](<Digital/ASUS/AUS2785/EFD3EC9DC84C>) |
| ASUS             | AUS2786 | VG27B            | 2560x1440 | 27.2 | 2023 | [C867C3615B94](<Digital/ASUS/AUS2786/C867C3615B94>) |
| ASUS             | AUS2786 | VG27B            | 2560x1440 | 27.2 | 2021 | [5A7DA3096B39](<Digital/ASUS/AUS2786/5A7DA3096B39>) |
| ASUS             | AUS2786 | VG27B            | 2560x1440 | 27.2 | 2019 | [5B28C5436ABA](<Digital/ASUS/AUS2786/5B28C5436ABA>) |
| ASUS             | AUS2787 | VG27VQ           | 1920x1080 | 27.2 | 2022 | [2247125EE312](<Digital/ASUS/AUS2787/2247125EE312>) |
| ASUS             | AUS2787 | VG27VQ           | 1920x1080 | 27.2 | 2021 | [8DD7A0C02286](<Digital/ASUS/AUS2787/8DD7A0C02286>) |
| ASUS             | AUS2787 | VG27VQ           | 1920x1080 | 27.2 | 2020 | [121F4031D2CB](<Digital/ASUS/AUS2787/121F4031D2CB>) |
| ASUS             | AUS2788 | PG279QE          | 2560x1440 | 27.2 | 2020 | [B65FD2BA1939](<Digital/ASUS/AUS2788/B65FD2BA1939>) |
| ASUS             | AUS2788 | PG279QE          | 2560x1440 | 27.2 | 2019 | [A17BA359DA39](<Digital/ASUS/AUS2788/A17BA359DA39>) |
| ASUS             | AUS2789 | PG279QE          | 2560x1440 | 27.2 |      | [EA82496CD312](<Digital/ASUS/AUS2789/EA82496CD312>) |
| ASUS             | AUS278A | PB278QV          | 2560x1440 | 27.2 | 2021 | [0236CB03FD69](<Digital/ASUS/AUS278A/0236CB03FD69>) |
| ASUS             | AUS278A | PB278QV          | 2560x1440 | 27.2 | 2020 | [1776791EBF9F](<Digital/ASUS/AUS278A/1776791EBF9F>) |
| ASUS             | AUS278A | PB278QV          | 2560x1440 | 27.2 | 2019 | [32524E0516D5](<Digital/ASUS/AUS278A/32524E0516D5>) |
| ASUS             | AUS278D | ROG XG279Q       | 2560x1440 | 27.2 | 2020 | [13DF872551F4](<Digital/ASUS/AUS278D/13DF872551F4>) |
| ASUS             | AUS278E | ROG XG279Q       | 2560x1440 | 27.2 | 2020 | [0CE9433C3C68](<Digital/ASUS/AUS278E/0CE9433C3C68>) |
| ASUS             | AUS278F | VG279QM          | 1920x1080 | 27.2 | 2024 | [0304BAC97B0C](<Digital/ASUS/AUS278F/0304BAC97B0C>) |
| ASUS             | AUS278F | VG279QM          | 1920x1080 | 27.2 | 2023 | [19E1CA6F129B](<Digital/ASUS/AUS278F/19E1CA6F129B>) |
| ASUS             | AUS278F | VG279QM          | 1920x1080 | 27.2 | 2022 | [1BA8F55C14F7](<Digital/ASUS/AUS278F/1BA8F55C14F7>) |
| ASUS             | AUS278F | VG279QM          | 1920x1080 | 27.2 | 2021 | [1D7D89351826](<Digital/ASUS/AUS278F/1D7D89351826>) |
| ASUS             | AUS278F | VG279QM          | 1920x1080 | 27.2 | 2020 | [1752172EEA68](<Digital/ASUS/AUS278F/1752172EEA68>) |
| ASUS             | AUS2792 | VA27AQ           | 2560x1440 | 27.2 | 2025 | [EFC762D6A6B9](<Digital/ASUS/AUS2792/EFC762D6A6B9>) |
| ASUS             | AUS279A | BE279QFK         | 1920x1080 | 27.2 | 2024 | [3934E449B7A8](<Digital/ASUS/AUS279A/3934E449B7A8>) |
| ASUS             | AUS27A1 | PB27U            | 3840x2160 | 27.2 | 2018 | [0C31666671FD](<Digital/ASUS/AUS27A1/0C31666671FD>) |
| ASUS             | AUS27A1 | PB27U            | 3840x2160 | 27.2 | 2017 | [5EA35E3826C5](<Digital/ASUS/AUS27A1/5EA35E3826C5>) |
| ASUS             | AUS27A1 |                  | 3840x2160 | 27.2 |      | [1A784A759682](<Digital/ASUS/AUS27A1/1A784A759682>) |
| ASUS             | AUS27A2 | MX27UC           | 3840x2160 | 27.2 | 2020 | [B28DDCA38858](<Digital/ASUS/AUS27A2/B28DDCA38858>) |
| ASUS             | AUS27A2 | MX27UC           | 3840x2160 | 27.2 | 2018 | [07014FB65429](<Digital/ASUS/AUS27A2/07014FB65429>) |
| ASUS             | AUS27A2 | MX27UC           | 3840x2160 | 27.2 | 2017 | [02CCA298543B](<Digital/ASUS/AUS27A2/02CCA298543B>) |
| ASUS             | AUS27A3 | VZ27A            | 2560x1440 | 27.2 | 2017 | [1481D90A4DAA](<Digital/ASUS/AUS27A3/1481D90A4DAA>) |
| ASUS             | AUS27A4 | ROG PG27U        | 3840x2160 | 27.2 | 2018 | [E66D62D81747](<Digital/ASUS/AUS27A4/E66D62D81747>) |
| ASUS             | AUS27A4 | ROG PG27U        | 3840x2160 | 27.2 |      | [3CC9C4EBB497](<Digital/ASUS/AUS27A4/3CC9C4EBB497>) |
| ASUS             | AUS27A5 | VZ27V            | 1920x1080 | 27.2 | 2019 | [CBB981D705DC](<Digital/ASUS/AUS27A5/CBB981D705DC>) |
| ASUS             | AUS27A5 | VZ27V            | 1920x1080 | 27.2 | 2018 | [2710286C116A](<Digital/ASUS/AUS27A5/2710286C116A>) |
| ASUS             | AUS27A5 | VZ27V            | 1920x1080 | 27.2 | 2017 | [1C160B975973](<Digital/ASUS/AUS27A5/1C160B975973>) |
| ASUS             | AUS27A6 | XG27VQ           | 1920x1080 | 27.2 | 2020 | [F51404C113EB](<Digital/ASUS/AUS27A6/F51404C113EB>) |
| ASUS             | AUS27A6 | XG27VQ           | 1920x1080 | 27.2 | 2019 | [D304CDA55CDD](<Digital/ASUS/AUS27A6/D304CDA55CDD>) |
| ASUS             | AUS27A6 | XG27VQ           | 1920x1080 | 27.2 | 2018 | [1339A32086B2](<Digital/ASUS/AUS27A6/1339A32086B2>) |
| ASUS             | AUS27A6 | XG27VQ           | 1920x1080 | 27.2 |      | [1D357B1D50E2](<Digital/ASUS/AUS27A6/1D357B1D50E2>) |
| ASUS             | AUS27A7 | BE27A            | 2560x1440 | 27.2 | 2020 | [5A4CF163BFFB](<Digital/ASUS/AUS27A7/5A4CF163BFFB>) |
| ASUS             | AUS27A7 | BE27A            | 2560x1440 | 27.2 | 2019 | [8BFA727AEFEB](<Digital/ASUS/AUS27A7/8BFA727AEFEB>) |
| ASUS             | AUS27A7 | BE27A            | 2560x1440 | 27.2 | 2017 | [449B1A4402E4](<Digital/ASUS/AUS27A7/449B1A4402E4>) |
| ASUS             | AUS27A9 | VZ27A            | 2560x1440 | 27.2 | 2018 | [5F0B2FCAE7A7](<Digital/ASUS/AUS27A9/5F0B2FCAE7A7>) |
| ASUS             | AUS27A9 | VZ27A            | 2560x1440 | 27.2 | 2017 | [0EF296947464](<Digital/ASUS/AUS27A9/0EF296947464>) |
| ASUS             | AUS27AA | VG275            | 1920x1080 | 27.2 | 2021 | [6A116940B2BA](<Digital/ASUS/AUS27AA/6A116940B2BA>) |
| ASUS             | AUS27AA | VG275            | 1920x1080 | 27.2 | 2017 | [27C43B82DB06](<Digital/ASUS/AUS27AA/27C43B82DB06>) |
| ASUS             | AUS27AB | VG275            | 1920x1080 | 27.2 | 2021 | [6F5ABE2D5B0C](<Digital/ASUS/AUS27AB/6F5ABE2D5B0C>) |
| ASUS             | AUS27AB | VG275            | 1920x1080 | 27.2 | 2019 | [802EE483B7B7](<Digital/ASUS/AUS27AB/802EE483B7B7>) |
| ASUS             | AUS27AB | VG275            | 1920x1080 | 27.2 | 2018 | [494AE3F02043](<Digital/ASUS/AUS27AB/494AE3F02043>) |
| ASUS             | AUS27AC | MZ27AQ           | 2560x1440 | 27.2 |      | [166B2B4129C3](<Digital/ASUS/AUS27AC/166B2B4129C3>) |
| ASUS             | AUS27AD | VG278            | 1920x1080 | 27.2 | 2021 | [23D14BEBC9DD](<Digital/ASUS/AUS27AD/23D14BEBC9DD>) |
| ASUS             | AUS27AD | VG278            | 1920x1080 | 27.2 | 2020 | [0EFA5CEE9591](<Digital/ASUS/AUS27AD/0EFA5CEE9591>) |
| ASUS             | AUS27AD | VG278            | 1920x1080 | 27.2 | 2019 | [00B0B9F38133](<Digital/ASUS/AUS27AD/00B0B9F38133>) |
| ASUS             | AUS27AD | VG278            | 1920x1080 | 27.2 | 2018 | [1DB2079F037C](<Digital/ASUS/AUS27AD/1DB2079F037C>) |
| ASUS             | AUS27AD | VG278            | 1920x1080 | 27.2 | 2017 | [DEC4795131B9](<Digital/ASUS/AUS27AD/DEC4795131B9>) |
| ASUS             | AUS27AD | VG278            | 1920x1080 | 27.2 |      | [0E4789E50297](<Digital/ASUS/AUS27AD/0E4789E50297>) |
| ASUS             | AUS27AE | VP278            | 1920x1080 | 27.2 | 2021 | [67A57D396F83](<Digital/ASUS/AUS27AE/67A57D396F83>) |
| ASUS             | AUS27AE | VP278            | 1920x1080 | 27.2 | 2020 | [4FB9A490F387](<Digital/ASUS/AUS27AE/4FB9A490F387>) |
| ASUS             | AUS27AE | VP278            | 1920x1080 | 27.2 | 2019 | [3BB764C7B042](<Digital/ASUS/AUS27AE/3BB764C7B042>) |
| ASUS             | AUS27AE | VP278            | 1920x1080 | 27.2 | 2018 | [05E2FDD68B06](<Digital/ASUS/AUS27AE/05E2FDD68B06>) |
| ASUS             | AUS27AE | VP278            | 1920x1080 | 27.2 | 2017 | [31C98619F365](<Digital/ASUS/AUS27AE/31C98619F365>) |
| ASUS             | AUS27AE |                  | 1920x1080 | 27.2 |      | [6F3E5292D9FB](<Digital/ASUS/AUS27AE/6F3E5292D9FB>) |
| ASUS             | AUS27AF | VG278            | 1920x1080 | 27.2 | 2022 | [B584FA77DFFE](<Digital/ASUS/AUS27AF/B584FA77DFFE>) |
| ASUS             | AUS27AF | VG278            | 1920x1080 | 27.2 | 2021 | [D16E11CC2FB6](<Digital/ASUS/AUS27AF/D16E11CC2FB6>) |
| ASUS             | AUS27AF | VG278            | 1920x1080 | 27.2 | 2020 | [35FA65C8AF5A](<Digital/ASUS/AUS27AF/35FA65C8AF5A>) |
| ASUS             | AUS27AF | VG278            | 1920x1080 | 27.2 | 2019 | [00417A3427FF](<Digital/ASUS/AUS27AF/00417A3427FF>) |
| ASUS             | AUS27AF | VG278            | 1920x1080 | 27.2 | 2018 | [1D206B148664](<Digital/ASUS/AUS27AF/1D206B148664>) |
| ASUS             | AUS27AF | VG278            | 1920x1080 | 27.2 | 2017 | [120051EF76D2](<Digital/ASUS/AUS27AF/120051EF76D2>) |
| ASUS             | AUS27B1 | ROG PG278QR      | 2560x1440 | 27.2 | 2019 | [00E8D3EECD3C](<Digital/ASUS/AUS27B1/00E8D3EECD3C>) |
| ASUS             | AUS27B1 | ROG PG278QR      | 2560x1440 | 27.2 | 2018 | [39C49DE914D8](<Digital/ASUS/AUS27B1/39C49DE914D8>) |
| ASUS             | AUS27B1 | ROG PG278QR      | 2560x1440 | 27.2 | 2017 | [13294FAF4176](<Digital/ASUS/AUS27B1/13294FAF4176>) |
| ASUS             | AUS27B1 | ROG PG278QR      | 2560x1440 | 27.2 | 2016 | [265EA8218CD5](<Digital/ASUS/AUS27B1/265EA8218CD5>) |
| ASUS             | AUS27B2 | ROG PG278QR      | 2560x1440 | 27.2 | 2018 | [385DC93E7BD6](<Digital/ASUS/AUS27B2/385DC93E7BD6>) |
| ASUS             | AUS27B2 | ROG PG278QR      | 2560x1440 | 27.2 | 2017 | [5AA8073E0003](<Digital/ASUS/AUS27B2/5AA8073E0003>) |
| ASUS             | AUS27B2 | ROG              | 2560x1440 | 27.2 |      | [60C6A0D75726](<Digital/ASUS/AUS27B2/60C6A0D75726>) |
| ASUS             | AUS27B4 | ROG PG27V        | 2560x1440 | 27.7 | 2019 | [2300B099F7DA](<Digital/ASUS/AUS27B4/2300B099F7DA>) |
| ASUS             | AUS27B4 | ROG PG27V        | 2560x1440 | 27.7 | 2018 | [DF8B981074BF](<Digital/ASUS/AUS27B4/DF8B981074BF>) |
| ASUS             | AUS27B4 | ROG PG27V        | 2560x1440 | 27.7 | 2017 | [EC28FF6B69ED](<Digital/ASUS/AUS27B4/EC28FF6B69ED>) |
| ASUS             | AUS27B6 | ROG PG278QE      | 2560x1440 | 27.2 | 2019 | [44939D31CCE6](<Digital/ASUS/AUS27B6/44939D31CCE6>) |
| ASUS             | AUS27BA | ROG XG27UQR      | 3840x2160 | 27.2 | 2023 | [465E8E2C5C1E](<Digital/ASUS/AUS27BA/465E8E2C5C1E>) |
| ASUS             | AUS27BA | ROG XG27UQR      | 3840x2160 | 27.2 | 2021 | [273A669F7622](<Digital/ASUS/AUS27BA/273A669F7622>) |
| ASUS             | AUS27BC | ROG PG27AQN      | 2560x1440 | 27.2 | 2041 | [7C884E2B9E1C](<Digital/ASUS/AUS27BC/7C884E2B9E1C>) |
| ASUS             | AUS27C0 | VZ279HE          | 1920x1080 | 27.2 | 2023 | [1563064C8D5E](<Digital/ASUS/AUS27C0/1563064C8D5E>) |
| ASUS             | AUS27C0 | VZ279HE          | 1920x1080 | 27.2 | 2022 | [34BCC81584FD](<Digital/ASUS/AUS27C0/34BCC81584FD>) |
| ASUS             | AUS27C0 | VZ279HE          | 1920x1080 | 27.2 | 2021 | [4B6E30D63C42](<Digital/ASUS/AUS27C0/4B6E30D63C42>) |
| ASUS             | AUS27C0 | VZ279HE          | 1920x1080 | 27.2 | 2020 | [02C52BFAAD40](<Digital/ASUS/AUS27C0/02C52BFAAD40>) |
| ASUS             | AUS27C0 | VZ279HE          | 1920x1080 | 27.2 | 2019 | [20ED40D2D909](<Digital/ASUS/AUS27C0/20ED40D2D909>) |
| ASUS             | AUS27C0 | VZ279HE          | 1920x1080 | 27.2 | 2018 | [0CA0F37F6C64](<Digital/ASUS/AUS27C0/0CA0F37F6C64>) |
| ASUS             | AUS27C0 | VZ279            | 1920x1080 | 27.2 | 2017 | [886E49582A0C](<Digital/ASUS/AUS27C0/886E49582A0C>) |
| ASUS             | AUS27C0 |                  | 1920x1080 | 27.2 |      | [57EA75A04026](<Digital/ASUS/AUS27C0/57EA75A04026>) |
| ASUS             | AUS27C1 | VZ279HE          | 1920x1080 | 27.2 | 2020 | [716B64449CF2](<Digital/ASUS/AUS27C1/716B64449CF2>) |
| ASUS             | AUS27C1 | VZ279            | 1920x1080 | 27.2 | 2019 | [4DEFFF9153D1](<Digital/ASUS/AUS27C1/4DEFFF9153D1>) |
| ASUS             | AUS27C1 | VZ279            | 1920x1080 | 27.2 | 2018 | [0E9E4094A5BF](<Digital/ASUS/AUS27C1/0E9E4094A5BF>) |
| ASUS             | AUS27C2 | VL278            | 1920x1080 | 27.2 | 2020 | [44421008FA99](<Digital/ASUS/AUS27C2/44421008FA99>) |
| ASUS             | AUS27C2 | VL278            | 1920x1080 | 27.2 | 2019 | [47106D4571B7](<Digital/ASUS/AUS27C2/47106D4571B7>) |
| ASUS             | AUS27C3 | VG27V            | 1920x1080 | 27.2 | 2024 | [8276B954AC1D](<Digital/ASUS/AUS27C3/8276B954AC1D>) |
| ASUS             | AUS27C3 | VG27V            | 1920x1080 | 27.2 | 2021 | [43AEE579A08A](<Digital/ASUS/AUS27C3/43AEE579A08A>) |
| ASUS             | AUS27C3 | VG27V            | 1920x1080 | 27.2 | 2020 | [06732379E667](<Digital/ASUS/AUS27C3/06732379E667>) |
| ASUS             | AUS27C3 | MX279            | 1920x1080 | 27.2 | 2019 | [427C654A8902](<Digital/ASUS/AUS27C3/427C654A8902>) |
| ASUS             | AUS27C3 | MX279            | 1920x1080 | 27.2 | 2018 | [782E251B903C](<Digital/ASUS/AUS27C3/782E251B903C>) |
| ASUS             | AUS27C3 |                  | 1920x1080 | 27.2 |      | [BCF55B7F1CBF](<Digital/ASUS/AUS27C3/BCF55B7F1CBF>) |
| ASUS             | AUS27C4 | VA27EQSB         | 1920x1080 | 27.2 | 2023 | [2BA5EE62B4ED](<Digital/ASUS/AUS27C4/2BA5EE62B4ED>) |
| ASUS             | AUS27C4 | VC279            | 1920x1080 | 27.2 | 2019 | [29D7FE767F50](<Digital/ASUS/AUS27C4/29D7FE767F50>) |
| ASUS             | AUS27C4 | VC279            | 1920x1080 | 27.2 | 2018 | [05CE8F782E08](<Digital/ASUS/AUS27C4/05CE8F782E08>) |
| ASUS             | AUS27C4 | VC279            | 1920x1080 | 27.2 |      | [97FEBC1059B1](<Digital/ASUS/AUS27C4/97FEBC1059B1>) |
| ASUS             | AUS27C7 | VA27UQSB         | 3840x2160 | 27.2 | 2023 | [99D04F4FE102](<Digital/ASUS/AUS27C7/99D04F4FE102>) |
| ASUS             | AUS27C9 | VZ279QG1R        | 1920x1080 | 23.4 | 2023 | [EB3FBD8F16AD](<Digital/ASUS/AUS27C9/EB3FBD8F16AD>) |
| ASUS             | AUS27CA | MZ279            | 1920x1080 | 27.2 | 2020 | [6E67CCD31ED6](<Digital/ASUS/AUS27CA/6E67CCD31ED6>) |
| ASUS             | AUS27D0 | VY279HGR         | 1920x1080 | 27.2 | 2025 | [06CC289492F1](<Digital/ASUS/AUS27D0/06CC289492F1>) |
| ASUS             | AUS27D0 | VY279HGR         | 1920x1080 | 27.2 | 2024 | [08839F1B2F0B](<Digital/ASUS/AUS27D0/08839F1B2F0B>) |
| ASUS             | AUS27D1 | VA279            | 1920x1080 | 27.2 | 2023 | [959DCE2F3FB2](<Digital/ASUS/AUS27D1/959DCE2F3FB2>) |
| ASUS             | AUS27D1 | VA279            | 1920x1080 | 27.2 | 2022 | [014203C3D1B4](<Digital/ASUS/AUS27D1/014203C3D1B4>) |
| ASUS             | AUS27D1 | VA279            | 1920x1080 | 27.2 | 2019 | [3A8016647FB9](<Digital/ASUS/AUS27D1/3A8016647FB9>) |
| ASUS             | AUS27D1 | VA279            | 1920x1080 | 27.2 | 2018 | [512CAF4C2C56](<Digital/ASUS/AUS27D1/512CAF4C2C56>) |
| ASUS             | AUS27D1 | VA279            | 1920x1080 | 27.2 |      | [26956027147E](<Digital/ASUS/AUS27D1/26956027147E>) |
| ASUS             | AUS27D2 | VA27EHE          | 1920x1080 | 27.2 | 2023 | [0716F18D0C9E](<Digital/ASUS/AUS27D2/0716F18D0C9E>) |
| ASUS             | AUS27D2 | VA27EHE          | 1920x1080 | 27.2 | 2022 | [009D3409E5C0](<Digital/ASUS/AUS27D2/009D3409E5C0>) |
| ASUS             | AUS27D2 | VA27EHE          | 1920x1080 | 27.2 | 2021 | [10E6053C1943](<Digital/ASUS/AUS27D2/10E6053C1943>) |
| ASUS             | AUS27D2 | VA27EHE          | 1920x1080 | 27.2 | 2020 | [01E34249E578](<Digital/ASUS/AUS27D2/01E34249E578>) |
| ASUS             | AUS27D2 | VA27EHE          | 1920x1080 | 27.2 | 2019 | [31027010FD3E](<Digital/ASUS/AUS27D2/31027010FD3E>) |
| ASUS             | AUS27D3 | VZ27EHF          | 1920x1080 | 27.2 | 2025 | [455E967339E2](<Digital/ASUS/AUS27D3/455E967339E2>) |
| ASUS             | AUS27D3 | VZ27EHF          | 1920x1080 | 27.2 | 2024 | [0F07432C780E](<Digital/ASUS/AUS27D3/0F07432C780E>) |
| ASUS             | AUS27D3 | VZ27EHF          | 1920x1080 | 27.2 | 2023 | [08A2D1CE8366](<Digital/ASUS/AUS27D3/08A2D1CE8366>) |
| ASUS             | AUS27D4 | VZ279HEG1R       | 1920x1080 | 27.2 | 2023 | [6B63BE4C6BB9](<Digital/ASUS/AUS27D4/6B63BE4C6BB9>) |
| ASUS             | AUS27D4 | VZ279HEG1R       | 1920x1080 | 27.2 | 2021 | [55DDF1F3A351](<Digital/ASUS/AUS27D4/55DDF1F3A351>) |
| ASUS             | AUS27D5 | VY279HF          | 1920x1080 | 27.2 | 2024 | [7B192F649567](<Digital/ASUS/AUS27D5/7B192F649567>) |
| ASUS             | AUS27D5 | VY279HF          | 1920x1080 | 27.2 | 2023 | [A87D5C2EE7AA](<Digital/ASUS/AUS27D5/A87D5C2EE7AA>) |
| ASUS             | AUS27D6 | VZ27EHE          | 1920x1080 | 27.2 | 2023 | [6B52007AEA07](<Digital/ASUS/AUS27D6/6B52007AEA07>) |
| ASUS             | AUS27D6 | VZ27EHE          | 1920x1080 | 27.2 | 2022 | [20031C23AD6C](<Digital/ASUS/AUS27D6/20031C23AD6C>) |
| ASUS             | AUS27DA | VY279            | 1920x1080 | 27.2 | 2024 | [9C1EE3BE2348](<Digital/ASUS/AUS27DA/9C1EE3BE2348>) |
| ASUS             | AUS27DA | VY279            | 1920x1080 | 27.2 | 2023 | [FB28EFF0CC9C](<Digital/ASUS/AUS27DA/FB28EFF0CC9C>) |
| ASUS             | AUS27DA | VY279            | 1920x1080 | 27.2 | 2022 | [A2E42942CC44](<Digital/ASUS/AUS27DA/A2E42942CC44>) |
| ASUS             | AUS27DA | VY279            | 1920x1080 | 27.2 | 2021 | [0E285D791CAD](<Digital/ASUS/AUS27DA/0E285D791CAD>) |
| ASUS             | AUS27DA | VY279            | 1920x1080 | 27.2 | 2020 | [1EF1E1FC9043](<Digital/ASUS/AUS27DA/1EF1E1FC9043>) |
| ASUS             | AUS27DD | VP279            | 1920x1080 | 27.2 | 2022 | [BAD7C77CE190](<Digital/ASUS/AUS27DD/BAD7C77CE190>) |
| ASUS             | AUS27DD | VP279            | 1920x1080 | 27.2 | 2021 | [64C364E4F649](<Digital/ASUS/AUS27DD/64C364E4F649>) |
| ASUS             | AUS27DD | VP279            | 1920x1080 | 27.2 | 2020 | [40F7CB841C41](<Digital/ASUS/AUS27DD/40F7CB841C41>) |
| ASUS             | AUS27DE | VY279HGE         | 1920x1080 | 27.2 | 2023 | [10662ED5C040](<Digital/ASUS/AUS27DE/10662ED5C040>) |
| ASUS             | AUS27DF | VP279            | 1920x1080 | 27.2 | 2020 | [45E09EC8B3D9](<Digital/ASUS/AUS27DF/45E09EC8B3D9>) |
| ASUS             | AUS27E0 | VG27WQ1B         | 2560x1440 | 27.2 | 2024 | [29DA8D40AAC4](<Digital/ASUS/AUS27E0/29DA8D40AAC4>) |
| ASUS             | AUS27E0 | VG27WQ1B         | 2560x1440 | 27.2 | 2023 | [3713ED0696E2](<Digital/ASUS/AUS27E0/3713ED0696E2>) |
| ASUS             | AUS27E0 | VG27W            | 2560x1440 | 27.2 | 2022 | [1E25B9CE0E66](<Digital/ASUS/AUS27E0/1E25B9CE0E66>) |
| ASUS             | AUS27E0 | VG27W            | 2560x1440 | 27.2 | 2021 | [14135E8BC5E4](<Digital/ASUS/AUS27E0/14135E8BC5E4>) |
| ASUS             | AUS27E0 | VG27W            | 2560x1440 | 27.2 | 2020 | [04DDE686DC71](<Digital/ASUS/AUS27E0/04DDE686DC71>) |
| ASUS             | AUS27E1 | PA279CRV         | 3840x2160 | 27.2 | 2024 | [93C929E31B94](<Digital/ASUS/AUS27E1/93C929E31B94>) |
| ASUS             | AUS27E1 | PA279CRV         | 3840x2160 | 27.2 | 2023 | [013D1FF4E043](<Digital/ASUS/AUS27E1/013D1FF4E043>) |
| ASUS             | AUS27E4 | VX279            | 1920x1080 | 27.2 | 2020 | [42B06F042573](<Digital/ASUS/AUS27E4/42B06F042573>) |
| ASUS             | AUS27E4 | VX279            | 1920x1080 | 27.2 | 2019 | [185EB9D5A21B](<Digital/ASUS/AUS27E4/185EB9D5A21B>) |
| ASUS             | AUS27E4 | VX279            | 1920x1080 | 27.2 |      | [1303F2FF360D](<Digital/ASUS/AUS27E4/1303F2FF360D>) |
| ASUS             | AUS27EA | VG27VQM          | 1920x1080 | 27.2 | 2044 | [BA4A166FF1A5](<Digital/ASUS/AUS27EA/BA4A166FF1A5>) |
| ASUS             | AUS27EA | VG27VQM          | 1920x1080 | 27.2 | 2024 | [1A5FE6B6D490](<Digital/ASUS/AUS27EA/1A5FE6B6D490>) |
| ASUS             | AUS27EA | VG27VQM          | 1920x1080 | 27.2 | 2022 | [E4BB6CB96053](<Digital/ASUS/AUS27EA/E4BB6CB96053>) |
| ASUS             | AUS27ED | PA278CGV         | 2560x1440 | 27.2 | 2024 | [3E2E94E50EDB](<Digital/ASUS/AUS27ED/3E2E94E50EDB>) |
| ASUS             | AUS27ED | PA278CGV         | 2560x1440 | 27.2 | 2023 | [342B5F1BBDDB](<Digital/ASUS/AUS27ED/342B5F1BBDDB>) |
| ASUS             | AUS27EE | VG27AQML1A       | 2560x1440 | 27.2 | 2024 | [9319B2CBBA3B](<Digital/ASUS/AUS27EE/9319B2CBBA3B>) |
| ASUS             | AUS27EE | VG27AQML1A       | 2560x1440 | 27.2 | 2023 | [11496565A740](<Digital/ASUS/AUS27EE/11496565A740>) |
| ASUS             | AUS27EF | VG27AQ3A         | 2560x1440 | 27.2 | 2025 | [C725AF708EA8](<Digital/ASUS/AUS27EF/C725AF708EA8>) |
| ASUS             | AUS27EF | VG27AQ3A         | 2560x1440 | 27.2 | 2024 | [231FBEFA128E](<Digital/ASUS/AUS27EF/231FBEFA128E>) |
| ASUS             | AUS27EF | VG27AQ3A         | 2560x1440 | 27.2 | 2023 | [11981C55028C](<Digital/ASUS/AUS27EF/11981C55028C>) |
| ASUS             | AUS27F0 | VG27AQ3A         | 2560x1440 | 27.2 | 2023 | [13E53169D069](<Digital/ASUS/AUS27F0/13E53169D069>) |
| ASUS             | AUS27F1 | XG27ACG          | 2560x1440 | 27.2 | 2024 | [23DB66FAE9B0](<Digital/ASUS/AUS27F1/23DB66FAE9B0>) |
| ASUS             | AUS27F2 | XG27AQDMG        | 2560x1440 | 26.6 | 2025 | [91707F662B1D](<Digital/ASUS/AUS27F2/91707F662B1D>) |
| ASUS             | AUS27F2 | XG27AQDMG        | 1920x1080 | 26.6 | 2025 | [A2DAEA445AEB](<Digital/ASUS/AUS27F2/A2DAEA445AEB>) |
| ASUS             | AUS27F2 | XG27AQDMG        | 2560x1440 | 26.6 | 2024 | [131EE1C1139D](<Digital/ASUS/AUS27F2/131EE1C1139D>) |
| ASUS             | AUS27F2 | XG27AQDMG        | 1920x1080 | 26.6 | 2024 | [AB3855E7D352](<Digital/ASUS/AUS27F2/AB3855E7D352>) |
| ASUS             | AUS27F4 | XG27ACDNG        | 2560x1440 | 26.6 | 2025 | [38C6A2F960CE](<Digital/ASUS/AUS27F4/38C6A2F960CE>) |
| ASUS             | AUS27F4 | XG27ACDNG        | 2560x1440 | 26.6 | 2024 | [2CCE70019FBF](<Digital/ASUS/AUS27F4/2CCE70019FBF>) |
| ASUS             | AUS27F5 | PG27UCDM         | 3840x2160 | 26.6 | 2025 | [874C9D170212](<Digital/ASUS/AUS27F5/874C9D170212>) |
| ASUS             | AUS27F6 | XG27UCDMG        | 3840x2160 | 26.6 | 2025 | [4B7B5866DCD9](<Digital/ASUS/AUS27F6/4B7B5866DCD9>) |
| ASUS             | AUS27FA | VG27AQA1A        | 2560x1440 | 27.2 | 2025 | [3B039B36B2E6](<Digital/ASUS/AUS27FA/3B039B36B2E6>) |
| ASUS             | AUS27FA | VG27AQA1A        | 2560x1440 | 27.2 | 2024 | [448EC05DAFA6](<Digital/ASUS/AUS27FA/448EC05DAFA6>) |
| ASUS             | AUS27FA | VG27AQA1A        | 2560x1440 | 27.2 | 2023 | [6FFBA1E6CE34](<Digital/ASUS/AUS27FA/6FFBA1E6CE34>) |
| ASUS             | AUS27FC | XG27AQV          | 2560x1440 | 27.2 | 2023 | [0ABED3D2B55F](<Digital/ASUS/AUS27FC/0ABED3D2B55F>) |
| ASUS             | AUS27FD | PG27AQDM         | 2560x1440 | 27.3 | 2024 | [9F2C62416040](<Digital/ASUS/AUS27FD/9F2C62416040>) |
| ASUS             | AUS27FD | PG27AQDM         | 2560x1440 | 27.3 | 2023 | [3479F5F62221](<Digital/ASUS/AUS27FD/3479F5F62221>) |
| ASUS             | AUS27FD | PG27AQDM         | 1920x1080 | 27.3 | 2023 | [4EEC02877A5A](<Digital/ASUS/AUS27FD/4EEC02877A5A>) |
| ASUS             | AUS27FD | PG27AQDM         | 2560x1440 | 27.3 | 2022 | [587C4B984FE1](<Digital/ASUS/AUS27FD/587C4B984FE1>) |
| ASUS             | AUS27FE | XG27ACS          | 2560x1440 | 27.2 | 2023 | [24172DD84278](<Digital/ASUS/AUS27FE/24172DD84278>) |
| ASUS             | AUS28A0 | VG28UQL1A        | 3840x2160 | 27.8 | 2021 | [01DE57BD0D75](<Digital/ASUS/AUS28A0/01DE57BD0D75>) |
| ASUS             | AUS28B1 | VP28U            | 3840x2160 | 27.8 | 2022 | [24C5DF0BF54E](<Digital/ASUS/AUS28B1/24C5DF0BF54E>) |
| ASUS             | AUS28B1 | VP28U            | 3840x2160 | 27.8 | 2021 | [0888FB1E39FC](<Digital/ASUS/AUS28B1/0888FB1E39FC>) |
| ASUS             | AUS28B1 | VP28U            | 3840x2160 | 27.8 | 2020 | [01B87E4A03DE](<Digital/ASUS/AUS28B1/01B87E4A03DE>) |
| ASUS             | AUS28B1 | VP28U            | 3840x2160 | 27.8 | 2019 | [054A1A59EB23](<Digital/ASUS/AUS28B1/054A1A59EB23>) |
| ASUS             | AUS28B1 | VP28U            | 3840x2160 | 27.8 | 2018 | [010559EE2BDB](<Digital/ASUS/AUS28B1/010559EE2BDB>) |
| ASUS             | AUS28B1 | VP28U            | 3840x2160 | 27.8 | 2017 | [0631FDE4D966](<Digital/ASUS/AUS28B1/0631FDE4D966>) |
| ASUS             | AUS28B1 |                  | 3840x2160 | 27.8 |      | [2537CBDC7DDC](<Digital/ASUS/AUS28B1/2537CBDC7DDC>) |
| ASUS             | AUS28BA | VG289            | 3840x2160 | 27.8 | 2023 | [2570510D9274](<Digital/ASUS/AUS28BA/2570510D9274>) |
| ASUS             | AUS28BA | VG289            | 3840x2160 | 27.8 | 2022 | [000B53A8D0CA](<Digital/ASUS/AUS28BA/000B53A8D0CA>) |
| ASUS             | AUS28BA | VG289            | 3840x2160 | 27.8 | 2021 | [05E1F40AFDE6](<Digital/ASUS/AUS28BA/05E1F40AFDE6>) |
| ASUS             | AUS28BA | VG289            | 3840x2160 | 27.8 | 2020 | [022192D8EB5F](<Digital/ASUS/AUS28BA/022192D8EB5F>) |
| ASUS             | AUS28BA | VG289            | 3840x2160 | 27.8 | 2019 | [1C404284E661](<Digital/ASUS/AUS28BA/1C404284E661>) |
| ASUS             | AUS28BA |                  | 3840x2160 | 27.8 |      | [73719BE18166](<Digital/ASUS/AUS28BA/73719BE18166>) |
| ASUS             | AUS28CA | VG289Q1A         | 3840x2160 | 27.8 | 2023 | [032FBACA8B1C](<Digital/ASUS/AUS28CA/032FBACA8B1C>) |
| ASUS             | AUS28CA | VG289Q1A         | 3840x2160 | 27.8 | 2022 | [122CFA4ACBDF](<Digital/ASUS/AUS28CA/122CFA4ACBDF>) |
| ASUS             | AUS28CA | VG289Q1A         | 2560x1440 | 27.8 | 2022 | [5EAE9BD6907F](<Digital/ASUS/AUS28CA/5EAE9BD6907F>) |
| ASUS             | AUS28CA | VG289Q1A         | 3840x1080 | 27.8 | 2022 | [EA772BC80B38](<Digital/ASUS/AUS28CA/EA772BC80B38>) |
| ASUS             | AUS28CA | VG289Q1A         | 3840x2160 | 27.8 | 2021 | [111CF7AE7912](<Digital/ASUS/AUS28CA/111CF7AE7912>) |
| ASUS             | AUS28CA | VG289Q1A         | 3840x2160 | 27.8 | 2020 | [0958CB33623B](<Digital/ASUS/AUS28CA/0958CB33623B>) |
| ASUS             | AUS28E0 | VP289Q           | 3840x2160 | 27.8 | 2023 | [1A25DEF0CD74](<Digital/ASUS/AUS28E0/1A25DEF0CD74>) |
| ASUS             | AUS2930 | VP299CL          | 2560x1080 | 28.6 | 2021 | [25E67DF7923B](<Digital/ASUS/AUS2930/25E67DF7923B>) |
| ASUS             | AUS3031 | XG309CM          | 2560x1080 | 29.5 | 2025 | [A83DBE8ADA81](<Digital/ASUS/AUS3031/A83DBE8ADA81>) |
| ASUS             | AUS3031 | XG309CM          | 2560x1080 | 29.5 | 2022 | [9E9A46F455D7](<Digital/ASUS/AUS3031/9E9A46F455D7>) |
| ASUS             | AUS3031 | XG309CM          | 2560x1080 | 29.5 | 2021 | [50EEADB48643](<Digital/ASUS/AUS3031/50EEADB48643>) |
| ASUS             | AUS303A | VG30VQL1A        | 2560x1080 | 29.5 | 2022 | [0E34B2E804FA](<Digital/ASUS/AUS303A/0E34B2E804FA>) |
| ASUS             | AUS303A | VG30VQL1A        | 2560x1080 | 29.5 | 2021 | [1D7D8585BF78](<Digital/ASUS/AUS303A/1D7D8585BF78>) |
| ASUS             | AUS3200 | PA329CRV         | 3840x2160 | 31.5 | 2025 | [A41412048706](<Digital/ASUS/AUS3200/A41412048706>) |
| ASUS             | AUS3200 | PA329CRV         | 3840x2160 | 31.5 | 2024 | [EC6C3325A502](<Digital/ASUS/AUS3200/EC6C3325A502>) |
| ASUS             | AUS3201 | VG32AQL1A        | 2560x1440 | 31.7 | 2023 | [91F00B1A59FD](<Digital/ASUS/AUS3201/91F00B1A59FD>) |
| ASUS             | AUS3201 | VG32AQL1A        | 2560x1440 | 31.7 | 2021 | [C9FD8FAC4875](<Digital/ASUS/AUS3201/C9FD8FAC4875>) |
| ASUS             | AUS3202 | VG32AQL1A        | 2560x1440 | 31.7 | 2023 | [3CF54D087A42](<Digital/ASUS/AUS3202/3CF54D087A42>) |
| ASUS             | AUS3202 | VG32AQL1A        | 2560x1440 | 31.7 | 2022 | [C80C26F5BF8E](<Digital/ASUS/AUS3202/C80C26F5BF8E>) |
| ASUS             | AUS3202 | VG32AQL1A        | 2560x1440 | 31.7 | 2021 | [89A5B5E3A848](<Digital/ASUS/AUS3202/89A5B5E3A848>) |
| ASUS             | AUS3207 | PA32UCDM         | 3840x2160 | 31.7 | 2025 | [25A85408FD0D](<Digital/ASUS/AUS3207/25A85408FD0D>) |
| ASUS             | AUS3220 | XG32VC           | 2560x1440 | 31.5 | 2021 | [13958F2BBC25](<Digital/ASUS/AUS3220/13958F2BBC25>) |
| ASUS             | AUS3220 | XG32VC           | 2560x1440 | 31.5 | 2020 | [C43F9EC8B36C](<Digital/ASUS/AUS3220/C43F9EC8B36C>) |
| ASUS             | AUS3227 | VA32UQSB         | 3840x2160 | 31.7 | 2024 | [26F528AFAC3A](<Digital/ASUS/AUS3227/26F528AFAC3A>) |
| ASUS             | AUS3228 | PG32UQXR         | 3840x2160 | 32.1 | 2023 | [855116698ADB](<Digital/ASUS/AUS3228/855116698ADB>) |
| ASUS             | AUS322E | PA329CV          | 3840x2160 | 31.7 | 2024 | [9138CCF604C4](<Digital/ASUS/AUS322E/9138CCF604C4>) |
| ASUS             | AUS322F | VP327Q           | 3840x2160 | 31.7 | 2025 | [8D688D9A1A6E](<Digital/ASUS/AUS322F/8D688D9A1A6E>) |
| ASUS             | AUS322F | VP327Q           | 3840x2160 | 31.7 | 2024 | [37D1251E3C5D](<Digital/ASUS/AUS322F/37D1251E3C5D>) |
| ASUS             | AUS3260 | PA32U            | 3840x2160 | 32.1 | 2020 | [00A3B3C94111](<Digital/ASUS/AUS3260/00A3B3C94111>) |
| ASUS             | AUS3260 | PA32U            | 3840x2160 | 32.1 | 2018 | [2A739069DB58](<Digital/ASUS/AUS3260/2A739069DB58>) |
| ASUS             | AUS3262 | PA32U            | 3840x2160 | 32.1 | 2018 | [CA09C0418FCC](<Digital/ASUS/AUS3262/CA09C0418FCC>) |
| ASUS             | AUS3263 | PA329C           | 3840x2160 | 32.1 | 2022 | [115E22C064AE](<Digital/ASUS/AUS3263/115E22C064AE>) |
| ASUS             | AUS3264 | PA329C           | 3840x2160 | 32.1 | 2021 | [919069191B12](<Digital/ASUS/AUS3264/919069191B12>) |
| ASUS             | AUS3264 | PA329C           | 3840x2160 | 32.1 | 2020 | [A262F3FE6ECD](<Digital/ASUS/AUS3264/A262F3FE6ECD>) |
| ASUS             | AUS3266 | PA32UCX          | 3840x2160 | 32.1 | 2021 | [B7EF9FEFBA4F](<Digital/ASUS/AUS3266/B7EF9FEFBA4F>) |
| ASUS             | AUS326C | PA328CGV         | 2560x1440 | 32.1 | 2023 | [E496F5AF4AD7](<Digital/ASUS/AUS326C/E496F5AF4AD7>) |
| ASUS             | AUS326C | PA328CGV         | 2560x1440 | 32.1 | 2022 | [09E55BF37883](<Digital/ASUS/AUS326C/09E55BF37883>) |
| ASUS             | AUS326D | PA328CGV         | 2560x1440 | 32.1 | 2023 | [73D652340E84](<Digital/ASUS/AUS326D/73D652340E84>) |
| ASUS             | AUS326D | PA328CGV         | 2560x1440 | 32.1 | 2022 | [E70421501C9C](<Digital/ASUS/AUS326D/E70421501C9C>) |
| ASUS             | AUS326D | PA328CGV         | 2560x1440 | 32.1 | 2021 | [C6727DEB4019](<Digital/ASUS/AUS326D/C6727DEB4019>) |
| ASUS             | AUS326E | PA329CV          | 3840x2160 | 32.1 | 2022 | [EB2ECCBE8507](<Digital/ASUS/AUS326E/EB2ECCBE8507>) |
| ASUS             | AUS326E | PA329CV          | 3840x2160 | 32.1 | 2021 | [20E1EA2ECC9D](<Digital/ASUS/AUS326E/20E1EA2ECC9D>) |
| ASUS             | AUS32A1 | VA32AQ           | 2560x1440 | 31.5 | 2018 | [090804E0D4C2](<Digital/ASUS/AUS32A1/090804E0D4C2>) |
| ASUS             | AUS32A1 | VA32AQ           | 2560x1440 | 31.5 | 2017 | [08FF1F2B9AEC](<Digital/ASUS/AUS32A1/08FF1F2B9AEC>) |
| ASUS             | AUS32A1 | VA32AQ           | 2560x1440 | 31.5 | 2016 | [92D60ED56C76](<Digital/ASUS/AUS32A1/92D60ED56C76>) |
| ASUS             | AUS32A1 | VA32AQ           | 2560x1440 | 31.5 |      | [21E6EF171EE0](<Digital/ASUS/AUS32A1/21E6EF171EE0>) |
| ASUS             | AUS32A2 | MX32V            | 2560x1440 | 31.5 | 2017 | [997D4ABEA324](<Digital/ASUS/AUS32A2/997D4ABEA324>) |
| ASUS             | AUS32A3 | VG32V            | 2560x1440 | 31.5 | 2022 | [D55DA1A32AAE](<Digital/ASUS/AUS32A3/D55DA1A32AAE>) |
| ASUS             | AUS32A3 | VG32V            | 2560x1440 | 31.5 | 2021 | [172B31E24957](<Digital/ASUS/AUS32A3/172B31E24957>) |
| ASUS             | AUS32A3 | VG32V            | 2560x1440 | 31.5 | 2020 | [051465B9C046](<Digital/ASUS/AUS32A3/051465B9C046>) |
| ASUS             | AUS32A3 | VG32V            | 2560x1440 | 31.5 | 2019 | [2BD3E403D22E](<Digital/ASUS/AUS32A3/2BD3E403D22E>) |
| ASUS             | AUS32A3 |                  | 2560x1440 | 31.5 |      | [337B5D207AF5](<Digital/ASUS/AUS32A3/337B5D207AF5>) |
| ASUS             | AUS32A4 | VA32U            | 3840x2160 | 31.5 | 2021 | [AE0969069855](<Digital/ASUS/AUS32A4/AE0969069855>) |
| ASUS             | AUS32A4 | VA32U            | 3840x2160 | 31.5 | 2019 | [B8253EB6F672](<Digital/ASUS/AUS32A4/B8253EB6F672>) |
| ASUS             | AUS32A6 | VP32AQ           | 2560x1440 | 31.5 | 2024 | [79BD94B39B6D](<Digital/ASUS/AUS32A6/79BD94B39B6D>) |
| ASUS             | AUS32A6 | VP32AQ           | 2560x1440 | 31.5 | 2023 | [5C62E295122E](<Digital/ASUS/AUS32A6/5C62E295122E>) |
| ASUS             | AUS32A6 | VP32AQ           | 2560x1440 | 31.5 | 2022 | [2AFA72C11DB9](<Digital/ASUS/AUS32A6/2AFA72C11DB9>) |
| ASUS             | AUS32A6 | VP32AQ           | 2560x1440 | 31.5 | 2021 | [12801AC7880E](<Digital/ASUS/AUS32A6/12801AC7880E>) |
| ASUS             | AUS32A7 | VP32UQ           | 3840x2160 | 31.5 | 2023 | [4795EF6FD4AB](<Digital/ASUS/AUS32A7/4795EF6FD4AB>) |
| ASUS             | AUS32A7 | VP32UQ           | 3840x2160 | 31.5 | 2022 | [FC8848591B6F](<Digital/ASUS/AUS32A7/FC8848591B6F>) |
| ASUS             | AUS32A7 | VP32UQ           | 3840x2160 | 31.5 | 2021 | [0735DE065598](<Digital/ASUS/AUS32A7/0735DE065598>) |
| ASUS             | AUS32A7 | VP32UQ           | 3840x2160 | 31.5 | 2020 | [E8DB20769910](<Digital/ASUS/AUS32A7/E8DB20769910>) |
| ASUS             | AUS32A8 | VG32VQR          | 2560x1440 | 31.5 | 2024 | [385DC94809EA](<Digital/ASUS/AUS32A8/385DC94809EA>) |
| ASUS             | AUS32A8 | VG32VQR          | 2560x1440 | 31.5 | 2023 | [094ED16ADCDB](<Digital/ASUS/AUS32A8/094ED16ADCDB>) |
| ASUS             | AUS32A8 | VG32VQR          | 2560x1440 | 31.5 | 2022 | [54A65B118123](<Digital/ASUS/AUS32A8/54A65B118123>) |
| ASUS             | AUS32A8 | VG32VQR          | 2560x1440 | 31.5 | 2021 | [07E1B8F53212](<Digital/ASUS/AUS32A8/07E1B8F53212>) |
| ASUS             | AUS32AB | XG32AQ           | 2560x1440 | 32.1 | 2022 | [86AE84083554](<Digital/ASUS/AUS32AB/86AE84083554>) |
| ASUS             | AUS32AC | XG32UQ           | 3840x2160 | 31.5 | 2022 | [0DFF26A334C0](<Digital/ASUS/AUS32AC/0DFF26A334C0>) |
| ASUS             | AUS32AD | VG328QA1A        | 1920x1080 | 31.5 | 2023 | [1FA560490305](<Digital/ASUS/AUS32AD/1FA560490305>) |
| ASUS             | AUS32B1 | XG32V            | 2560x1440 | 31.5 | 2020 | [148150126065](<Digital/ASUS/AUS32B1/148150126065>) |
| ASUS             | AUS32B1 | XG32V            | 2560x1440 | 31.5 | 2019 | [16D0D162B423](<Digital/ASUS/AUS32B1/16D0D162B423>) |
| ASUS             | AUS32B1 | XG32V            | 2560x1440 | 31.5 | 2018 | [74AFA9BF1391](<Digital/ASUS/AUS32B1/74AFA9BF1391>) |
| ASUS             | AUS32B1 |                  | 2560x1440 | 31.5 |      | [8460E7A823AF](<Digital/ASUS/AUS32B1/8460E7A823AF>) |
| ASUS             | AUS32B2 | XG32VQR          | 2560x1440 | 31.5 | 2020 | [80059C33B2B4](<Digital/ASUS/AUS32B2/80059C33B2B4>) |
| ASUS             | AUS32B2 | XG32VQR          | 2560x1440 | 31.5 | 2019 | [07A9230BB733](<Digital/ASUS/AUS32B2/07A9230BB733>) |
| ASUS             | AUS32B2 |                  | 2560x1440 | 31.5 |      | [A768883B886C](<Digital/ASUS/AUS32B2/A768883B886C>) |
| ASUS             | AUS32B4 | ROG PG32UQX      | 3840x2160 | 32.1 | 2021 | [D53B8BC9DD91](<Digital/ASUS/AUS32B4/D53B8BC9DD91>) |
| ASUS             | AUS32B8 | VG32AQA1A        | 2560x1440 | 31.5 | 2024 | [31B0E1ACFF43](<Digital/ASUS/AUS32B8/31B0E1ACFF43>) |
| ASUS             | AUS32B8 | VG32AQA1A        | 2560x1440 | 31.5 | 2023 | [08CCAD08103E](<Digital/ASUS/AUS32B8/08CCAD08103E>) |
| ASUS             | AUS32B8 | VG32AQA1A        | 2560x1440 | 31.5 | 2022 | [35D52E8C3429](<Digital/ASUS/AUS32B8/35D52E8C3429>) |
| ASUS             | AUS32BB | XG32WCMS         | 2560x1440 | 31.5 | 2024 | [DA10F6C50439](<Digital/ASUS/AUS32BB/DA10F6C50439>) |
| ASUS             | AUS32C3 | VG328            | 1920x1080 | 31.5 | 2023 | [94CFCAC4D398](<Digital/ASUS/AUS32C3/94CFCAC4D398>) |
| ASUS             | AUS32C3 | VG328            | 1920x1080 | 31.5 | 2022 | [9F8D267153C8](<Digital/ASUS/AUS32C3/9F8D267153C8>) |
| ASUS             | AUS32C3 | VG328            | 1920x1080 | 31.5 | 2020 | [90D69C5D6AB3](<Digital/ASUS/AUS32C3/90D69C5D6AB3>) |
| ASUS             | AUS32D0 | VA329HE          | 1920x1080 | 31.5 | 2023 | [1347652CADA1](<Digital/ASUS/AUS32D0/1347652CADA1>) |
| ASUS             | AUS32DA | VA326            | 1920x1080 | 31.5 | 2020 | [D415F34B1087](<Digital/ASUS/AUS32DA/D415F34B1087>) |
| ASUS             | AUS32DA | VA326            | 1920x1080 | 31.5 | 2019 | [82356551B9F9](<Digital/ASUS/AUS32DA/82356551B9F9>) |
| ASUS             | AUS32E0 | VG32VQ1B         | 2560x1440 | 31.5 | 2025 | [E52DC79C8C0C](<Digital/ASUS/AUS32E0/E52DC79C8C0C>) |
| ASUS             | AUS32E0 | VG32VQ1B         | 2560x1440 | 31.5 | 2024 | [240517AC9783](<Digital/ASUS/AUS32E0/240517AC9783>) |
| ASUS             | AUS32E0 | VG32VQ1B         | 2560x1440 | 31.5 | 2023 | [1957A993614E](<Digital/ASUS/AUS32E0/1957A993614E>) |
| ASUS             | AUS32E0 | VG32VQ1B         | 2560x1440 | 31.5 | 2022 | [55F91D009446](<Digital/ASUS/AUS32E0/55F91D009446>) |
| ASUS             | AUS32E0 |                  | 2560x1440 | 31.5 | 2021 | [05F3FC661B07](<Digital/ASUS/AUS32E0/05F3FC661B07>) |
| ASUS             | AUS32E0 | VG32VQ1B         | 2560x1440 | 31.5 | 2020 | [0C2CE896DAC2](<Digital/ASUS/AUS32E0/0C2CE896DAC2>) |
| ASUS             | AUS32E1 | PG32UQ           | 3840x2160 | 32.1 | 2022 | [74C7BCF98FFB](<Digital/ASUS/AUS32E1/74C7BCF98FFB>) |
| ASUS             | AUS32E1 | PG32UQ           | 3840x2160 | 32.1 | 2021 | [5E0113F570D1](<Digital/ASUS/AUS32E1/5E0113F570D1>) |
| ASUS             | AUS32E1 | PG32UQ           | 3840x2160 | 32.1 | 2020 | [32DA65AB5A80](<Digital/ASUS/AUS32E1/32DA65AB5A80>) |
| ASUS             | AUS32EA | VG32UQA1A        | 3840x2160 | 31.5 | 2023 | [8830F0AF4407](<Digital/ASUS/AUS32EA/8830F0AF4407>) |
| ASUS             | AUS32F2 | PG32UCDM         | 3840x2160 | 31.7 | 2025 | [336F48020011](<Digital/ASUS/AUS32F2/336F48020011>) |
| ASUS             | AUS32F2 | PG32UCDM         | 3840x2160 | 31.7 | 2024 | [0D4BFE100FD5](<Digital/ASUS/AUS32F2/0D4BFE100FD5>) |
| ASUS             | AUS32F3 | PG329            | 2560x1440 | 32.1 | 2021 | [206E93261BBA](<Digital/ASUS/AUS32F3/206E93261BBA>) |
| ASUS             | AUS32F3 | PG329            | 2560x1440 | 32.1 | 2020 | [08A5CFE38CA2](<Digital/ASUS/AUS32F3/08A5CFE38CA2>) |
| ASUS             | AUS32F4 | PG32UCDP         | 3840x2160 | 31.7 | 2024 | [6966E5CAAF12](<Digital/ASUS/AUS32F4/6966E5CAAF12>) |
| ASUS             | AUS32FA | VA326            | 1920x1080 | 31.5 | 2018 | [DFC9045B85BF](<Digital/ASUS/AUS32FA/DFC9045B85BF>) |
| ASUS             | AUS32FA | VA326            | 1920x1080 | 31.5 | 2017 | [670EE32DA0FE](<Digital/ASUS/AUS32FA/670EE32DA0FE>) |
| ASUS             | AUS32FA | VA326            | 1920x1080 | 31.5 | 2016 | [22F041756EC3](<Digital/ASUS/AUS32FA/22F041756EC3>) |
| ASUS             | AUS342A | PG34WCDM         | 3440x1440 | 34.1 | 2024 | [D850FC333AA5](<Digital/ASUS/AUS342A/D850FC333AA5>) |
| ASUS             | AUS342A | PG34WCDM         | 3440x1440 | 34.1 | 2023 | [6E8196EBC063](<Digital/ASUS/AUS342A/6E8196EBC063>) |
| ASUS             | AUS342E | PA348CGV         | 3440x1440 | 34.2 | 2024 | [173F3934FBBF](<Digital/ASUS/AUS342E/173F3934FBBF>) |
| ASUS             | AUS342E | PA348CGV         | 3440x1440 | 34.2 | 2022 | [182C87601697](<Digital/ASUS/AUS342E/182C87601697>) |
| ASUS             | AUS3431 | MX34V            | 3440x1440 | 34.1 | 2018 | [FEFD12612590](<Digital/ASUS/AUS3431/FEFD12612590>) |
| ASUS             | AUS3431 | MX34V            | 3440x1440 | 34.1 | 2017 | [71F28BF522C8](<Digital/ASUS/AUS3431/71F28BF522C8>) |
| ASUS             | AUS3431 |                  | 3440x1440 | 34.1 |      | [D6D0DDA2D681](<Digital/ASUS/AUS3431/D6D0DDA2D681>) |
| ASUS             | AUS3432 | PA34V            | 3440x1440 | 34.2 | 2019 | [5D71C9AC345D](<Digital/ASUS/AUS3432/5D71C9AC345D>) |
| ASUS             | AUS3435 | VG34V            | 3440x1440 | 34.1 | 2024 | [0F6619256D78](<Digital/ASUS/AUS3435/0F6619256D78>) |
| ASUS             | AUS3435 | VG34V            | 3440x1440 | 34.1 | 2023 | [21A7C4560C76](<Digital/ASUS/AUS3435/21A7C4560C76>) |
| ASUS             | AUS3435 | VG34V            | 3440x1440 | 34.1 | 2022 | [3CA438F6E3A8](<Digital/ASUS/AUS3435/3CA438F6E3A8>) |
| ASUS             | AUS3435 | VG34V            | 3440x1440 | 34.1 | 2021 | [66848840A45E](<Digital/ASUS/AUS3435/66848840A45E>) |
| ASUS             | AUS3435 | VG34V            | 3440x1440 | 34.1 | 2020 | [4C291191C3FA](<Digital/ASUS/AUS3435/4C291191C3FA>) |
| ASUS             | AUS3438 | VG34VQL3A        | 3440x1440 | 34.2 | 2025 | [6585ADE436D4](<Digital/ASUS/AUS3438/6585ADE436D4>) |
| ASUS             | AUS3438 | VG34VQL3A        | 3440x1440 | 34.2 | 2024 | [1AAAD5EFD8A8](<Digital/ASUS/AUS3438/1AAAD5EFD8A8>) |
| ASUS             | AUS3438 | VG34VQL3A        | 3440x1440 | 34.2 | 2023 | [258B7D502538](<Digital/ASUS/AUS3438/258B7D502538>) |
| ASUS             | AUS3439 | VP349CGL         | 3440x1440 | 34.4 | 2024 | [D37B5A854186](<Digital/ASUS/AUS3439/D37B5A854186>) |
| ASUS             | AUS3439 | VP349CGL         | 3440x1440 | 34.4 | 2022 | [091FA912A788](<Digital/ASUS/AUS3439/091FA912A788>) |
| ASUS             | AUS3439 | VP349CGL         | 3440x1440 | 34.4 | 2021 | [D914D7F521F5](<Digital/ASUS/AUS3439/D914D7F521F5>) |
| ASUS             | AUS343B | PG349Q           | 3440x1440 | 34.2 | 2019 | [75273275A7E8](<Digital/ASUS/AUS343B/75273275A7E8>) |
| ASUS             | AUS343C | VP348            | 3440x1440 | 34.2 | 2020 | [1972AF48CA1F](<Digital/ASUS/AUS343C/1972AF48CA1F>) |
| ASUS             | AUS343C | VP348            | 3440x1440 | 34.2 | 2019 | [3C2D2164419C](<Digital/ASUS/AUS343C/3C2D2164419C>) |
| ASUS             | AUS343F | VG34VQEL1A       | 3440x1440 | 33.9 | 2024 | [95D3FBA9E4A3](<Digital/ASUS/AUS343F/95D3FBA9E4A3>) |
| ASUS             | AUS343F | VG34VQEL1A       | 3440x1440 | 33.9 | 2023 | [14DB2E633D1E](<Digital/ASUS/AUS343F/14DB2E633D1E>) |
| ASUS             | AUS343F | VG34VQEL1A       | 3440x1440 | 33.9 | 2022 | [7B7951AB8FF0](<Digital/ASUS/AUS343F/7B7951AB8FF0>) |
| ASUS             | AUS3453 | VG34VQ3B         | 3440x1440 | 34.1 | 2023 | [112982236B97](<Digital/ASUS/AUS3453/112982236B97>) |
| ASUS             | AUS346A | XG349C           | 3440x1440 | 34.4 | 2023 | [1AFD14E4F21B](<Digital/ASUS/AUS346A/1AFD14E4F21B>) |
| ASUS             | AUS346A | XG349C           | 3440x1440 | 34.4 | 2021 | [605B3D3504AA](<Digital/ASUS/AUS346A/605B3D3504AA>) |
| ASUS             | AUS346A | XG349C           | 3440x1440 | 34.4 | 2020 | [3270F93C4ACB](<Digital/ASUS/AUS346A/3270F93C4ACB>) |
| ASUS             | AUS3551 | XG35V            | 3440x1440 | 35.1 | 2019 | [4C844AC5B095](<Digital/ASUS/AUS3551/4C844AC5B095>) |
| ASUS             | AUS3551 | XG35V            | 3440x1440 | 35.1 | 2018 | [270275C93420](<Digital/ASUS/AUS3551/270275C93420>) |
| ASUS             | AUS3551 | XG35V            | 3440x1440 | 35.1 | 2017 | [5BF0AE7AB23E](<Digital/ASUS/AUS3551/5BF0AE7AB23E>) |
| ASUS             | AUS3553 | ROG PG35V        | 3440x1440 | 34.7 | 2020 | [1F6B755EFEF5](<Digital/ASUS/AUS3553/1F6B755EFEF5>) |
| ASUS             | AUS3554 | VG35V            | 3440x1440 | 35.1 | 2021 | [2B471091358B](<Digital/ASUS/AUS3554/2B471091358B>) |
| ASUS             | AUS3554 | VG35V            | 3440x1440 | 35.1 | 2020 | [0E5A867D3E5D](<Digital/ASUS/AUS3554/0E5A867D3E5D>) |
| ASUS             | AUS3554 | VG35V            | 3440x1440 | 35.1 | 2019 | [9F46283DC5E9](<Digital/ASUS/AUS3554/9F46283DC5E9>) |
| ASUS             | AUS3831 | MX38V            | 3840x1600 | 37.6 | 2019 | [E0E64343B920](<Digital/ASUS/AUS3831/E0E64343B920>) |
| ASUS             | AUS38EA | PG38UQ           | 3840x2160 | 37.9 | 2022 | [091554B1A0E2](<Digital/ASUS/AUS38EA/091554B1A0E2>) |
| ASUS             | AUS42E0 | PG42UQ           | 3840x2160 | 41.6 | 2022 | [09F3B7B7CA58](<Digital/ASUS/AUS42E0/09F3B7B7CA58>) |
| ASUS             | AUS4390 | XG43V            | 3840x1200 | 43.3 | 2021 | [7E38470ADD5E](<Digital/ASUS/AUS4390/7E38470ADD5E>) |
| ASUS             | AUS4390 | XG43V            | 3840x1200 | 43.3 | 2020 | [3153F47A57DE](<Digital/ASUS/AUS4390/3153F47A57DE>) |
| ASUS             | AUS4390 |                  | 3840x1200 | 43.3 |      | [D3BD0B326E68](<Digital/ASUS/AUS4390/D3BD0B326E68>) |
| ASUS             | AUS43A0 | XG43UQ           | 3840x2160 | 42.5 | 2020 | [056824F61107](<Digital/ASUS/AUS43A0/056824F61107>) |
| ASUS             | AUS43A1 | PG43U            | 3840x2160 | 42.5 | 2021 | [8AE0AD6352CF](<Digital/ASUS/AUS43A1/8AE0AD6352CF>) |
| ASUS             | AUS43A1 | PG43U            | 3840x2160 | 42.5 | 2020 | [4CD1AD8768C4](<Digital/ASUS/AUS43A1/4CD1AD8768C4>) |
| ASUS             | AUS43A1 | PG43U            | 3840x2160 | 42.5 | 2019 | [585D7B8DFBBE](<Digital/ASUS/AUS43A1/585D7B8DFBBE>) |
| ASUS             | AUS43E1 | XG438            | 3840x2160 | 42.5 | 2021 | [34F3ADCB1801](<Digital/ASUS/AUS43E1/34F3ADCB1801>) |
| ASUS             | AUS43E1 | XG438            | 3840x2160 | 42.5 | 2020 | [16490DB48EF6](<Digital/ASUS/AUS43E1/16490DB48EF6>) |
| ASUS             | AUS43E1 | XG438            | 3840x2160 | 42.5 | 2019 | [316C54F14B72](<Digital/ASUS/AUS43E1/316C54F14B72>) |
| ASUS             | AUS48E0 | PG48UQ           | 3840x2160 | 27.2 | 2022 | [7628DFC1CF4A](<Digital/ASUS/AUS48E0/7628DFC1CF4A>) |
| ASUS             | AUS48E0 | PG48UQ           | 3840x2160 | 31.5 | 2022 | [9D6E221405D7](<Digital/ASUS/AUS48E0/9D6E221405D7>) |
| ASUS             | AUS48E0 | PG48UQ           | 3840x2160 | 31.5 | 1990 | [27029C49BE5C](<Digital/ASUS/AUS48E0/27029C49BE5C>) |
| ASUS             | AUS4921 | PG49WCD          | 3840x1080 | 48.7 | 2023 | [784A1B132543](<Digital/ASUS/AUS4921/784A1B132543>) |
| ASUS             | AUS4932 | XG49WCR          | 3840x1080 | 48.7 | 2022 | [136684C8AF32](<Digital/ASUS/AUS4932/136684C8AF32>) |
| ASUS             | AUS49A1 | XG49V            | 3840x1080 | 49.1 | 2023 | [694B95E3D99E](<Digital/ASUS/AUS49A1/694B95E3D99E>) |
| ASUS             | AUS49A1 | XG49V            | 3840x1080 | 49.1 | 2022 | [6B2CBF506DF4](<Digital/ASUS/AUS49A1/6B2CBF506DF4>) |
| ASUS             | AUS49A1 | XG49V            | 3840x1080 | 49.1 | 2021 | [0DDCC2762F17](<Digital/ASUS/AUS49A1/0DDCC2762F17>) |
| ASUS             | AUS49A1 | XG49V            | 3840x1080 | 49.1 | 2020 | [9091AF236472](<Digital/ASUS/AUS49A1/9091AF236472>) |
| ASUS             | AUS49A1 | XG49V            | 3840x1080 | 49.1 | 2019 | [14E4C404BB4B](<Digital/ASUS/AUS49A1/14E4C404BB4B>) |
| ASUS             | AUS65A1 | ROG PG65UQ       | 3840x2160 | 64.5 | 2019 | [1C01397B22A6](<Digital/ASUS/AUS65A1/1C01397B22A6>) |
| ASUS             | AUSAA06 | XG32UCWMG        | 3840x2160 | 31.5 | 2025 | [84D76A11CB90](<Digital/ASUS/AUSAA06/84D76A11CB90>) |
| ASUS             | AUSAA08 | PG32UCDMR        | 3840x2160 | 31.5 | 2025 | [76805148F993](<Digital/ASUS/AUSAA08/76805148F993>) |
| ASUS             | WWW282C | ZN242IF          | 1920x1080 | 21.7 | 2017 | [75C7D5091939](<Digital/ASUS/WWW282C/75C7D5091939>) |
| ASUS             | WWW282C | ZN242GD          | 1920x1080 | 24.2 | 2017 | [9AADE38E3451](<Digital/ASUS/WWW282C/9AADE38E3451>) |
| AU Optronics     | AUO0000 | faytech          | 1920x1080 | 21.1 | 2012 | [EB3657DC7A83](<Digital/AU Optronics/AUO0000/EB3657DC7A83>) |
| AU Optronics     | AUO0014 | B140EW01V0       | 1280x768  | 15.2 | 2004 | [DDDA6BD6BACB](<Digital/AU Optronics/AUO0014/DDDA6BD6BACB>) |
| AU Optronics     | AUO0025 | M240HW02 V5      | 1920x1080 | 24.0 | 2010 | [64FA0F5C526E](<Digital/AU Optronics/AUO0025/64FA0F5C526E>) |
| AU Optronics     | AUO00C9 | M201SP01         | 1680x1050 | 20.0 | 2006 | [282FE3AB9B85](<Digital/AU Optronics/AUO00C9/282FE3AB9B85>) |
| AU Optronics     | AUO00ED | 6985X            | 1920x1080 | 15.3 | 2011 | [3EEEA5903D3D](<Digital/AU Optronics/AUO00ED/3EEEA5903D3D>) |
| AU Optronics     | AUO0100 |                  | 1920x1080 |      | 2022 | [D38D0B130850](<Digital/AU Optronics/AUO0100/D38D0B130850>) |
| AU Optronics     | AUO0114 | B140EW01V1 B1... | 1280x768  | 15.2 |      | [20BCEC5DBBC4](<Digital/AU Optronics/AUO0114/20BCEC5DBBC4>) |
| AU Optronics     | AUO019C |                  | 1920x1200 | 13.4 | 2021 | [FC1013A8EE1B](<Digital/AU Optronics/AUO019C/FC1013A8EE1B>) |
| AU Optronics     | AUO01EE | B156RW01 V1      | 1600x900  | 15.3 | 2008 | [4AD0A1347398](<Digital/AU Optronics/AUO01EE/4AD0A1347398>) |
| AU Optronics     | AUO0290 |                  | 1366x768  | 13.9 | 2020 | [5D04A3CC45EE](<Digital/AU Optronics/AUO0290/5D04A3CC45EE>) |
| AU Optronics     | AUO0291 | B156HAB03.1      | 1920x1080 | 15.3 | 2019 | [BBC30DACB4DE](<Digital/AU Optronics/AUO0291/BBC30DACB4DE>) |
| AU Optronics     | AUO029E | B173RW01 V2      | 1600x900  | 17.1 | 2009 | [ADF0FF1C04DD](<Digital/AU Optronics/AUO029E/ADF0FF1C04DD>) |
| AU Optronics     | AUO02EC | B156XW02 V2      | 1366x768  | 15.3 | 2009 | [816D057D1BA5](<Digital/AU Optronics/AUO02EC/816D057D1BA5>) |
| AU Optronics     | AUO038E | B156HAN10        | 1920x1080 | 15.3 |      | [4A2A5AC57504](<Digital/AU Optronics/AUO038E/4A2A5AC57504>) |
| AU Optronics     | AUO039E | B173RW01 V3      | 1600x900  | 17.1 | 2009 | [23189A212301](<Digital/AU Optronics/AUO039E/23189A212301>) |
| AU Optronics     | AUO048E | B156HAN10.2      | 1920x1080 | 15.3 | 2019 | [5DFC6955325B](<Digital/AU Optronics/AUO048E/5DFC6955325B>) |
| AU Optronics     | AUO04A4 |                  | 1920x1200 | 12.0 | 2022 | [01D8A05B3CEB](<Digital/AU Optronics/AUO04A4/01D8A05B3CEB>) |
| AU Optronics     | AUO05A7 | B156HTN06.1      | 1920x1080 | 15.3 | 2022 | [F3F72DBC1AFD](<Digital/AU Optronics/AUO05A7/F3F72DBC1AFD>) |
| AU Optronics     | AUO068B |                  | 1920x1080 | 13.9 | 2019 | [4BE49C95DA1C](<Digital/AU Optronics/AUO068B/4BE49C95DA1C>) |
| AU Optronics     | AUO0696 | B140HAN06.8      | 1920x1080 | 13.9 | 2020 | [4ADC612A53F2](<Digital/AU Optronics/AUO0696/4ADC612A53F2>) |
| AU Optronics     | AUO07B2 | B160QAN02.3      | 2560x1600 | 15.9 | 2024 | [6FFDBB25E454](<Digital/AU Optronics/AUO07B2/6FFDBB25E454>) |
| AU Optronics     | AUO08AF | RKGM2            | 1920x1080 | 13.9 | 2023 | [3B983E3221D6](<Digital/AU Optronics/AUO08AF/3B983E3221D6>) |
| AU Optronics     | AUO0908 | B160HW02 V0      | 1920x1080 | 15.9 | 2011 | [03F0DC7F4CF1](<Digital/AU Optronics/AUO0908/03F0DC7F4CF1>) |
| AU Optronics     | AUO0908 | B160HW02 V0      | 1920x1080 | 15.9 | 2010 | [9EAAC1A6DA6D](<Digital/AU Optronics/AUO0908/9EAAC1A6DA6D>) |
| AU Optronics     | AUO0A8C | F5VTJ            | 1366x768  | 15.3 | 2019 | [DF17E4E1E333](<Digital/AU Optronics/AUO0A8C/DF17E4E1E333>) |
| AU Optronics     | AUO0A97 |                  | 1920x1080 | 17.3 | 2020 | [F4C9C7987679](<Digital/AU Optronics/AUO0A97/F4C9C7987679>) |
| AU Optronics     | AUO0AB1 |                  | 1920x1080 | 15.3 | 2023 | [87AE2AE9FBB0](<Digital/AU Optronics/AUO0AB1/87AE2AE9FBB0>) |
| AU Optronics     | AUO0B93 | B140HAN04.0      | 1920x1080 | 13.9 | 2020 | [06F0ED1A9175](<Digital/AU Optronics/AUO0B93/06F0ED1A9175>) |
| AU Optronics     | AUO0B9E | B160UAN01.H      | 1920x1200 | 15.9 |      | [A998B0A347F9](<Digital/AU Optronics/AUO0B9E/A998B0A347F9>) |
| AU Optronics     | AUO0BA2 | B140QAN02.3      | 2560x1440 | 13.9 | 2021 | [2CC992B3BFF3](<Digital/AU Optronics/AUO0BA2/2CC992B3BFF3>) |
| AU Optronics     | AUO0C01 | B121EW01 Colo... | 1280x800  | 12.6 |      | [094A40C0F932](<Digital/AU Optronics/AUO0C01/094A40C0F932>) |
| AU Optronics     | AUO0C9C | B156HAN02.1      | 1920x1080 | 15.3 | 2019 | [E5E52DBDA351](<Digital/AU Optronics/AUO0C9C/E5E52DBDA351>) |
| AU Optronics     | AUO0D92 | X8RPY            | 1920x1080 | 15.0 | 2020 | [F820F00277A7](<Digital/AU Optronics/AUO0D92/F820F00277A7>) |
| AU Optronics     | AUO0F03 |                  | 1400x1050 | 14.9 |      | [50504AD767BF](<Digital/AU Optronics/AUO0F03/50504AD767BF>) |
| AU Optronics     | AUO0F06 |                  | 1024x768  | 14.9 | 2004 | [5A17D849BA16](<Digital/AU Optronics/AUO0F06/5A17D849BA16>) |
| AU Optronics     | AUO0F06 | B150XG01V2       | 1024x768  | 14.9 |      | [15D085CB64E9](<Digital/AU Optronics/AUO0F06/15D085CB64E9>) |
| AU Optronics     | AUO0F07 | D8381            | 1024x768  | 14.9 |      | [3F57B5A2441B](<Digital/AU Optronics/AUO0F07/3F57B5A2441B>) |
| AU Optronics     | AUO0F07 | B150XG02V1       | 1024x768  | 15.2 |      | [3F919B3B3E28](<Digital/AU Optronics/AUO0F07/3F919B3B3E28>) |
| AU Optronics     | AUO0F0D | B154EW01 V.7     | 1280x800  | 15.4 |      | [03416BEC573D](<Digital/AU Optronics/AUO0F0D/03416BEC573D>) |
| AU Optronics     | AUO0F93 | C1H8T            | 1920x1200 | 13.4 | 2020 | [52889EA52D61](<Digital/AU Optronics/AUO0F93/52889EA52D61>) |
| AU Optronics     | AUO0FA7 |                  | 2560x1600 | 14.0 | 2022 | [DFA8F9F72DF4](<Digital/AU Optronics/AUO0FA7/DFA8F9F72DF4>) |
| AU Optronics     | AUO0FB2 | B140UAN02.7      | 1920x1200 | 14.0 | 2024 | [74357E9B58F0](<Digital/AU Optronics/AUO0FB2/74357E9B58F0>) |
| AU Optronics     | AUO1013 |                  | 1128x1504 | 13.3 | 2018 | [9D46B496225E](<Digital/AU Optronics/AUO1013/9D46B496225E>) |
| AU Optronics     | AUO101A |                  | 3000x2000 | 12.8 | 2016 | [07FBAF811632](<Digital/AU Optronics/AUO101A/07FBAF811632>) |
| AU Optronics     | AUO1020 | A089SW01 V0      | 1024x600  | 8.6  | 2008 | [71D8B5F2D17F](<Digital/AU Optronics/AUO1020/71D8B5F2D17F>) |
| AU Optronics     | AUO102C | B133XTN01.0      | 1366x768  | 13.0 | 2012 | [E90D70F7FBEC](<Digital/AU Optronics/AUO102C/E90D70F7FBEC>) |
| AU Optronics     | AUO102C | B133XTF01.0      | 1366x768  | 13.0 | 2011 | [605D777F9DCA](<Digital/AU Optronics/AUO102C/605D777F9DCA>) |
| AU Optronics     | AUO102C |                  | 1366x768  | 13.0 | 2008 | [114C25D279AB](<Digital/AU Optronics/AUO102C/114C25D279AB>) |
| AU Optronics     | AUO102D | TG1WM            | 1920x1080 | 13.2 | 2019 | [D2323FC17BB3](<Digital/AU Optronics/AUO102D/D2323FC17BB3>) |
| AU Optronics     | AUO102D | 2XMJR            | 1920x1080 | 13.2 | 2018 | [C3BCF5687C5C](<Digital/AU Optronics/AUO102D/C3BCF5687C5C>) |
| AU Optronics     | AUO102D | RTK UHD HDR      | 3840x2160 | 26.9 | 2018 | [F439CBE47D51](<Digital/AU Optronics/AUO102D/F439CBE47D51>) |
| AU Optronics     | AUO102D | 4FHP9            | 1920x1080 | 13.2 | 2017 | [699CA9C790E4](<Digital/AU Optronics/AUO102D/699CA9C790E4>) |
| AU Optronics     | AUO102D | W94FJ            | 1920x1080 | 13.2 | 2016 | [0918037108B0](<Digital/AU Optronics/AUO102D/0918037108B0>) |
| AU Optronics     | AUO102D |                  | 1920x1080 | 13.2 | 2015 | [4994FEDAF0FE](<Digital/AU Optronics/AUO102D/4994FEDAF0FE>) |
| AU Optronics     | AUO1036 | F0WXV            | 2560x1440 | 13.9 | 2014 | [CD4F9138C683](<Digital/AU Optronics/AUO1036/CD4F9138C683>) |
| AU Optronics     | AUO103C |                  | 1366x768  | 13.9 | 2016 | [401EC3E5E7DB](<Digital/AU Optronics/AUO103C/401EC3E5E7DB>) |
| AU Optronics     | AUO103C |                  | 1366x768  | 13.9 | 2015 | [0184EFFAE31F](<Digital/AU Optronics/AUO103C/0184EFFAE31F>) |
| AU Optronics     | AUO103C |                  | 1366x768  | 13.9 | 2013 | [73E3CCE77F7C](<Digital/AU Optronics/AUO103C/73E3CCE77F7C>) |
| AU Optronics     | AUO103C | B140XTT01.0      | 1366x768  | 13.9 | 2012 | [6D96131F54AA](<Digital/AU Optronics/AUO103C/6D96131F54AA>) |
| AU Optronics     | AUO103C | C591J            | 1366x768  | 13.9 | 2009 | [0276F15D9748](<Digital/AU Optronics/AUO103C/0276F15D9748>) |
| AU Optronics     | AUO103C | B140XW01 V0      | 1366x768  | 13.9 | 2008 | [22F8D0D16BC6](<Digital/AU Optronics/AUO103C/22F8D0D16BC6>) |
| AU Optronics     | AUO103D | B140HAK01.0      | 1920x1080 | 13.9 | 2016 | [5E95CD634EA1](<Digital/AU Optronics/AUO103D/5E95CD634EA1>) |
| AU Optronics     | AUO103D |                  | 1920x1080 | 13.9 | 2015 | [1269671A58A2](<Digital/AU Optronics/AUO103D/1269671A58A2>) |
| AU Optronics     | AUO103D | TFVG5            | 1920x1080 | 13.9 | 2014 | [27EA3EF751EB](<Digital/AU Optronics/AUO103D/27EA3EF751EB>) |
| AU Optronics     | AUO103D | 1D28M            | 1920x1080 | 13.9 | 2013 | [58F02A065C16](<Digital/AU Optronics/AUO103D/58F02A065C16>) |
| AU Optronics     | AUO103E | W3V10            | 1600x900  | 13.9 | 2014 | [05FAA2F2133A](<Digital/AU Optronics/AUO103E/05FAA2F2133A>) |
| AU Optronics     | AUO103E |                  | 1600x900  | 13.9 | 2011 | [0AB7CCAB5656](<Digital/AU Optronics/AUO103E/0AB7CCAB5656>) |
| AU Optronics     | AUO103E | F133J            | 1600x900  | 13.9 | 2009 | [014C7C2D793C](<Digital/AU Optronics/AUO103E/014C7C2D793C>) |
| AU Optronics     | AUO1044 | DR503 #2>Fe      | 1280x800  | 14.0 | 2006 | [27740F8F7C05](<Digital/AU Optronics/AUO1044/27740F8F7C05>) |
| AU Optronics     | AUO1044 | J9370 '7CMo      | 1280x800  | 14.0 |      | [889F35BFAFBA](<Digital/AU Optronics/AUO1044/889F35BFAFBA>) |
| AU Optronics     | AUO1047 | UN087 0@MTv      | 1440x900  | 14.0 | 2006 | [9676AD1511EC](<Digital/AU Optronics/AUO1047/9676AD1511EC>) |
| AU Optronics     | AUO1047 | KC232 0@Hp       | 1440x900  | 14.0 |      | [F54F415CF543](<Digital/AU Optronics/AUO1047/F54F415CF543>) |
| AU Optronics     | AUO105C | 2G5VN            | 1366x768  | 11.6 | 2018 | [DA52F22A8553](<Digital/AU Optronics/AUO105C/DA52F22A8553>) |
| AU Optronics     | AUO105C | G7TKC            | 1366x768  | 11.6 | 2016 | [4037EA680C54](<Digital/AU Optronics/AUO105C/4037EA680C54>) |
| AU Optronics     | AUO105C |                  | 1366x768  | 11.6 | 2015 | [652CF3195888](<Digital/AU Optronics/AUO105C/652CF3195888>) |
| AU Optronics     | AUO105C | B116XTB01.0      | 1366x768  | 11.6 | 2014 | [6E2C8D05E491](<Digital/AU Optronics/AUO105C/6E2C8D05E491>) |
| AU Optronics     | AUO105C | B116XTN01.0      | 1366x768  | 11.6 | 2013 | [26F08BDEF9E4](<Digital/AU Optronics/AUO105C/26F08BDEF9E4>) |
| AU Optronics     | AUO105C | B116XTN01.0      | 1366x768  | 11.6 | 2011 | [A66407FF6386](<Digital/AU Optronics/AUO105C/A66407FF6386>) |
| AU Optronics     | AUO105C | B116XW01 V0      | 1366x768  | 11.6 | 2009 | [18DE76F3B17B](<Digital/AU Optronics/AUO105C/18DE76F3B17B>) |
| AU Optronics     | AUO105C | V1V85            | 1366x768  | 11.6 | 2008 | [08E613B415DE](<Digital/AU Optronics/AUO105C/08E613B415DE>) |
| AU Optronics     | AUO105C | 4CF14            | 1366x768  | 11.6 |      | [123F12A9347B](<Digital/AU Optronics/AUO105C/123F12A9347B>) |
| AU Optronics     | AUO1062 |                  | 1366x912  | 11.9 | 2018 | [00AAF6F321E2](<Digital/AU Optronics/AUO1062/00AAF6F321E2>) |
| AU Optronics     | AUO1068 |                  | 1920x1200 | 12.2 | 2016 | [14ED5FDE3121](<Digital/AU Optronics/AUO1068/14ED5FDE3121>) |
| AU Optronics     | AUO106C | 9X5G1            | 1366x768  | 12.7 | 2016 | [98D96E89F434](<Digital/AU Optronics/AUO106C/98D96E89F434>) |
| AU Optronics     | AUO106C |                  | 1366x768  | 12.7 | 2014 | [C0CD3112BA39](<Digital/AU Optronics/AUO106C/C0CD3112BA39>) |
| AU Optronics     | AUO106C | V022P            | 1366x768  | 12.7 | 2013 | [272E3CEDFE3E](<Digital/AU Optronics/AUO106C/272E3CEDFE3E>) |
| AU Optronics     | AUO106C | B125XTN01.0      | 1366x768  | 12.7 | 2012 | [7EEB31935C84](<Digital/AU Optronics/AUO106C/7EEB31935C84>) |
| AU Optronics     | AUO106C | 8X9KT            | 1366x768  | 12.7 | 2011 | [FF2F8E3ACA2E](<Digital/AU Optronics/AUO106C/FF2F8E3ACA2E>) |
| AU Optronics     | AUO106C | B125XW01 V0      | 1366x768  | 12.7 | 2010 | [31E1A22B37ED](<Digital/AU Optronics/AUO106C/31E1A22B37ED>) |
| AU Optronics     | AUO106C | NH627            | 1366x768  | 12.7 |      | [940DDE008DE0](<Digital/AU Optronics/AUO106C/940DDE008DE0>) |
| AU Optronics     | AUO106D | G120YAT01.0      | 2880x1920 | 11.9 | 2018 | [0BC01113DC1C](<Digital/AU Optronics/AUO106D/0BC01113DC1C>) |
| AU Optronics     | AUO106D | B125HAK01.0      | 1920x1080 | 12.7 | 2017 | [F139173EA496](<Digital/AU Optronics/AUO106D/F139173EA496>) |
| AU Optronics     | AUO106D | B125HAN01.0      | 1920x1080 | 12.7 | 2014 | [10B17D3BBA14](<Digital/AU Optronics/AUO106D/10B17D3BBA14>) |
| AU Optronics     | AUO106F | B120YAN01.0      | 2880x1920 | 11.9 | 2016 | [5397F05F0797](<Digital/AU Optronics/AUO106F/5397F05F0797>) |
| AU Optronics     | AUO107D | J4VRV            | 1920x1080 | 15.0 | 2020 | [A29379F64006](<Digital/AU Optronics/AUO107D/A29379F64006>) |
| AU Optronics     | AUO1088 | B170UW01 V0      | 1920x1200 | 17.2 | 2007 | [B20CF959B2CF](<Digital/AU Optronics/AUO1088/B20CF959B2CF>) |
| AU Optronics     | AUO108F | G140JAN01.0      | 2160x1440 | 14.2 | 2020 | [62471951455E](<Digital/AU Optronics/AUO108F/62471951455E>) |
| AU Optronics     | AUO108F |                  | 1920x1080 | 13.2 | 2019 | [4243E2CDBA09](<Digital/AU Optronics/AUO108F/4243E2CDBA09>) |
| AU Optronics     | AUO1092 |                  | 1920x1080 | 15.3 | 2019 | [2F7313688CE9](<Digital/AU Optronics/AUO1092/2F7313688CE9>) |
| AU Optronics     | AUO1096 |                  | 2560x1440 | 17.1 | 2016 | [D64E15915ED1](<Digital/AU Optronics/AUO1096/D64E15915ED1>) |
| AU Optronics     | AUO109B | B173ZAN01.0      | 3840x2160 | 17.1 | 2017 | [E448241C2050](<Digital/AU Optronics/AUO109B/E448241C2050>) |
| AU Optronics     | AUO109B | 8CJK2            | 3840x2160 | 17.1 | 2015 | [7844576A15AB](<Digital/AU Optronics/AUO109B/7844576A15AB>) |
| AU Optronics     | AUO109D | NTY1H            | 1920x1080 | 17.1 | 2016 | [18E88AC792BA](<Digital/AU Optronics/AUO109D/18E88AC792BA>) |
| AU Optronics     | AUO109D | B173HAN01.0      | 1920x1080 | 17.1 | 2015 | [2B67EF3DBD38](<Digital/AU Optronics/AUO109D/2B67EF3DBD38>) |
| AU Optronics     | AUO109D | B173HAN01.0      | 1920x1080 | 17.1 | 2014 | [FF5336D88F4E](<Digital/AU Optronics/AUO109D/FF5336D88F4E>) |
| AU Optronics     | AUO109D | T197N            | 1920x1080 | 17.1 | 2009 | [0DE5B14EA880](<Digital/AU Optronics/AUO109D/0DE5B14EA880>) |
| AU Optronics     | AUO109D | B173HAN01        | 1920x1080 | 17.1 |      | [87E48D3E4351](<Digital/AU Optronics/AUO109D/87E48D3E4351>) |
| AU Optronics     | AUO109E | 4PG9N            | 1600x900  | 17.1 | 2009 | [0FA08A112785](<Digital/AU Optronics/AUO109E/0FA08A112785>) |
| AU Optronics     | AUO109E | B173RW01 V0      | 1600x900  | 17.1 | 2008 | [A6DF2214BD24](<Digital/AU Optronics/AUO109E/A6DF2214BD24>) |
| AU Optronics     | AUO10AB |                  | 1920x1200 | 15.9 | 2023 | [1F44F1031200](<Digital/AU Optronics/AUO10AB/1F44F1031200>) |
| AU Optronics     | AUO10AB |                  | 1680x1050 | 20.0 | 2007 | [CAF6C456CB43](<Digital/AU Optronics/AUO10AB/CAF6C456CB43>) |
| AU Optronics     | AUO10C2 | B089AW01 V0      | 1024x600  | 9.0  | 2008 | [0905D4B6C1AF](<Digital/AU Optronics/AUO10C2/0905D4B6C1AF>) |
| AU Optronics     | AUO10D1 | K253P            | 1024x576  | 10.1 | 2009 | [297ECFC86548](<Digital/AU Optronics/AUO10D1/297ECFC86548>) |
| AU Optronics     | AUO10D5 |                  | 1280x720  | 10.1 | 2009 | [C51D1C91209A](<Digital/AU Optronics/AUO10D5/C51D1C91209A>) |
| AU Optronics     | AUO10DC | B101XTN01.0      | 1366x768  | 10.1 | 2012 | [42DF24F5C34E](<Digital/AU Optronics/AUO10DC/42DF24F5C34E>) |
| AU Optronics     | AUO10EB | R5VC9            | 3840x2160 | 15.3 | 2019 | [FA6905E4D35E](<Digital/AU Optronics/AUO10EB/FA6905E4D35E>) |
| AU Optronics     | AUO10EC | B156XTK01.0      | 1366x768  | 15.3 | 2017 | [0F6F3A3F83DB](<Digital/AU Optronics/AUO10EC/0F6F3A3F83DB>) |
| AU Optronics     | AUO10EC | WWJY1            | 1366x768  | 15.3 | 2016 | [3E67D84B38FA](<Digital/AU Optronics/AUO10EC/3E67D84B38FA>) |
| AU Optronics     | AUO10EC | JJ45K            | 1366x768  | 15.3 | 2015 | [C8EB7CAC823E](<Digital/AU Optronics/AUO10EC/C8EB7CAC823E>) |
| AU Optronics     | AUO10EC | B156XTK01.0      | 1366x768  | 15.3 | 2014 | [14B03E98F165](<Digital/AU Optronics/AUO10EC/14B03E98F165>) |
| AU Optronics     | AUO10EC | RK2MD            | 1366x768  | 15.3 | 2013 | [5713BD81A26A](<Digital/AU Optronics/AUO10EC/5713BD81A26A>) |
| AU Optronics     | AUO10EC | B156XTT01.0      | 1366x768  | 15.3 | 2012 | [D9D90F0CEFAF](<Digital/AU Optronics/AUO10EC/D9D90F0CEFAF>) |
| AU Optronics     | AUO10EC | B156XTN01.0      | 1366x768  | 15.3 | 2011 | [7A434F1D37CA](<Digital/AU Optronics/AUO10EC/7A434F1D37CA>) |
| AU Optronics     | AUO10EC | B156XW01 V0      | 1366x768  | 15.3 | 2008 | [2EAE033FB0C3](<Digital/AU Optronics/AUO10EC/2EAE033FB0C3>) |
| AU Optronics     | AUO10ED | 0079Y            | 1920x1080 | 15.3 | 2016 | [387CBB3B1D9C](<Digital/AU Optronics/AUO10ED/387CBB3B1D9C>) |
| AU Optronics     | AUO10ED |                  | 1920x1080 | 15.3 | 2015 | [34CF21A7D660](<Digital/AU Optronics/AUO10ED/34CF21A7D660>) |
| AU Optronics     | AUO10ED | 9F8C8            | 1920x1080 | 15.3 | 2014 | [0A0C95F7974B](<Digital/AU Optronics/AUO10ED/0A0C95F7974B>) |
| AU Optronics     | AUO10ED | B156HTT01.0      | 1920x1080 | 15.3 | 2013 | [01AC2DEF4909](<Digital/AU Optronics/AUO10ED/01AC2DEF4909>) |
| AU Optronics     | AUO10ED | FTKKN            | 1920x1080 | 15.3 | 2012 | [F7D0A0F087C6](<Digital/AU Optronics/AUO10ED/F7D0A0F087C6>) |
| AU Optronics     | AUO10ED | B156HTN01.0      | 1920x1080 | 15.3 | 2011 | [5E208909EC2B](<Digital/AU Optronics/AUO10ED/5E208909EC2B>) |
| AU Optronics     | AUO10ED | F790K            | 1920x1080 | 15.3 | 2008 | [531265AC09CB](<Digital/AU Optronics/AUO10ED/531265AC09CB>) |
| AU Optronics     | AUO10ED | 0079Y            | 1920x1080 | 15.3 |      | [F4199C9AF827](<Digital/AU Optronics/AUO10ED/F4199C9AF827>) |
| AU Optronics     | AUO10EE | B156RW01         | 1600x900  | 15.3 |      | [024ADDA27582](<Digital/AU Optronics/AUO10EE/024ADDA27582>) |
| AU Optronics     | AUO1101 | B170PW01 V.1     | 1440x900  | 17.2 |      | [58EA09D576BD](<Digital/AU Optronics/AUO1101/58EA09D576BD>) |
| AU Optronics     | AUO112B | B133ZAN01.1      | 3840x2160 | 13.2 | 2016 | [7D7AA839A177](<Digital/AU Optronics/AUO112B/7D7AA839A177>) |
| AU Optronics     | AUO112C |                  | 1366x768  | 13.0 | 2008 | [3170B96D8212](<Digital/AU Optronics/AUO112C/3170B96D8212>) |
| AU Optronics     | AUO112D | B133HAK01.1      | 1920x1080 | 13.2 | 2016 | [FEA504CF686E](<Digital/AU Optronics/AUO112D/FEA504CF686E>) |
| AU Optronics     | AUO112D | B133HTN01.1      | 1920x1080 | 13.2 | 2013 | [20859B980A07](<Digital/AU Optronics/AUO112D/20859B980A07>) |
| AU Optronics     | AUO1136 |                  | 2560x1440 | 13.9 | 2014 | [01E42A6C7AFA](<Digital/AU Optronics/AUO1136/01E42A6C7AFA>) |
| AU Optronics     | AUO113B |                  | 3840x2160 | 13.9 | 2018 | [C97D79929B01](<Digital/AU Optronics/AUO113B/C97D79929B01>) |
| AU Optronics     | AUO113C |                  | 1366x768  | 13.9 | 2012 | [23B1743CF30D](<Digital/AU Optronics/AUO113C/23B1743CF30D>) |
| AU Optronics     | AUO113D |                  | 1920x1080 | 13.9 | 2017 | [8C22752B5963](<Digital/AU Optronics/AUO113D/8C22752B5963>) |
| AU Optronics     | AUO113D | D0PX9            | 1920x1080 | 13.9 | 2016 | [2D0E47F28F71](<Digital/AU Optronics/AUO113D/2D0E47F28F71>) |
| AU Optronics     | AUO113D | 75G6T            | 1920x1080 | 13.9 | 2013 | [4ECF5176072C](<Digital/AU Optronics/AUO113D/4ECF5176072C>) |
| AU Optronics     | AUO113D | B140HAN01.1      | 1920x1080 | 13.9 | 2012 | [7F5093F78145](<Digital/AU Optronics/AUO113D/7F5093F78145>) |
| AU Optronics     | AUO1144 | B141EW01 V1      | 1280x800  | 15.1 |      | [FE0E08205079](<Digital/AU Optronics/AUO1144/FE0E08205079>) |
| AU Optronics     | AUO1147 | B141PW01 V1      | 1440x900  | 14.0 | 2006 | [FFFC9E77FE6A](<Digital/AU Optronics/AUO1147/FFFC9E77FE6A>) |
| AU Optronics     | AUO115C |                  | 1366x768  | 11.6 | 2017 | [FD0B3F6DB735](<Digital/AU Optronics/AUO115C/FD0B3F6DB735>) |
| AU Optronics     | AUO115C |                  | 1366x768  | 11.6 | 2016 | [45E9AD0D67AF](<Digital/AU Optronics/AUO115C/45E9AD0D67AF>) |
| AU Optronics     | AUO115C | KY05P            | 1366x768  | 11.6 | 2014 | [87F85D22F282](<Digital/AU Optronics/AUO115C/87F85D22F282>) |
| AU Optronics     | AUO1188 |                  | 1920x1200 | 17.2 | 2007 | [28AD001884D5](<Digital/AU Optronics/AUO1188/28AD001884D5>) |
| AU Optronics     | AUO119B |                  | 3840x2160 | 17.1 | 2015 | [58D974B96C69](<Digital/AU Optronics/AUO119B/58D974B96C69>) |
| AU Optronics     | AUO119D | B173HAN01.1      | 1920x1080 | 17.1 | 2016 | [FC9DA2F38263](<Digital/AU Optronics/AUO119D/FC9DA2F38263>) |
| AU Optronics     | AUO119D | B173HTN01.1      | 1920x1080 | 17.1 | 2015 | [C6C2118288C2](<Digital/AU Optronics/AUO119D/C6C2118288C2>) |
| AU Optronics     | AUO119D | MM77H            | 1920x1080 | 17.1 | 2014 | [ED20FC2E3E4E](<Digital/AU Optronics/AUO119D/ED20FC2E3E4E>) |
| AU Optronics     | AUO119D | B173HTN01.1      | 1920x1080 | 17.1 | 2013 | [61411331739D](<Digital/AU Optronics/AUO119D/61411331739D>) |
| AU Optronics     | AUO119E | B173RTN01.1      | 1600x900  | 17.1 | 2014 | [E0C6D4FA2F0D](<Digital/AU Optronics/AUO119E/E0C6D4FA2F0D>) |
| AU Optronics     | AUO119E | 3V6TR            | 1600x900  | 17.1 | 2013 | [7D66D2F0E5D6](<Digital/AU Optronics/AUO119E/7D66D2F0E5D6>) |
| AU Optronics     | AUO119E | B173RTN01.1      | 1600x900  | 17.1 | 2011 | [559D7588C5F2](<Digital/AU Optronics/AUO119E/559D7588C5F2>) |
| AU Optronics     | AUO119E | B173RW01 V1      | 1600x900  | 17.1 | 2008 | [05CB3679C4ED](<Digital/AU Optronics/AUO119E/05CB3679C4ED>) |
| AU Optronics     | AUO11C2 | B089AW01 V1      | 1024x600  | 9.0  | 2008 | [1989CB2265AE](<Digital/AU Optronics/AUO11C2/1989CB2265AE>) |
| AU Optronics     | AUO11D1 | B101AW01 V1      | 1024x576  | 10.1 | 2009 | [65B6687DDDCD](<Digital/AU Optronics/AUO11D1/65B6687DDDCD>) |
| AU Optronics     | AUO11D1 | B101AW01 V1      | 1024x576  | 10.1 | 2008 | [E5174A948F0A](<Digital/AU Optronics/AUO11D1/E5174A948F0A>) |
| AU Optronics     | AUO11D5 | B101EW01         | 1280x720  | 10.1 |      | [A549AEC9F049](<Digital/AU Optronics/AUO11D5/A549AEC9F049>) |
| AU Optronics     | AUO11DC |                  | 1366x768  | 10.1 | 2013 | [4B0C55400F55](<Digital/AU Optronics/AUO11DC/4B0C55400F55>) |
| AU Optronics     | AUO11DC | B101XTN01.1      | 1366x768  | 10.1 | 2012 | [C963E82EFDDE](<Digital/AU Optronics/AUO11DC/C963E82EFDDE>) |
| AU Optronics     | AUO11EC | WGHK8            | 1366x768  | 15.3 | 2013 | [7869C5165486](<Digital/AU Optronics/AUO11EC/7869C5165486>) |
| AU Optronics     | AUO11EC | M094G            | 1366x768  | 15.3 | 2008 | [4E08D44B6B2D](<Digital/AU Optronics/AUO11EC/4E08D44B6B2D>) |
| AU Optronics     | AUO11ED | CRN6V            | 1920x1080 | 15.3 | 2014 | [2E6AFC3DB896](<Digital/AU Optronics/AUO11ED/2E6AFC3DB896>) |
| AU Optronics     | AUO11ED | B156HAN01.1      | 1920x1080 | 15.3 | 2013 | [18A434A33926](<Digital/AU Optronics/AUO11ED/18A434A33926>) |
| AU Optronics     | AUO11ED |                  | 1920x1080 | 15.3 | 2012 | [7D8C41714389](<Digital/AU Optronics/AUO11ED/7D8C41714389>) |
| AU Optronics     | AUO11ED | B156HW01 V1      | 1920x1080 | 15.3 | 2009 | [01C839F004C2](<Digital/AU Optronics/AUO11ED/01C839F004C2>) |
| AU Optronics     | AUO11EE | B173RTN01.1      | 1920x1080 | 17.1 | 2011 | [F5D44D47E73C](<Digital/AU Optronics/AUO11EE/F5D44D47E73C>) |
| AU Optronics     | AUO11EE |                  | 1600x900  | 15.3 | 2008 | [0D14F9938916](<Digital/AU Optronics/AUO11EE/0D14F9938916>) |
| AU Optronics     | AUO1224 | B133EW01 V2      | 1280x800  | 13.4 | 2006 | [9DA453E25176](<Digital/AU Optronics/AUO1224/9DA453E25176>) |
| AU Optronics     | AUO122C | B133XTN01.2      | 1366x768  | 13.0 | 2011 | [52AB56B29C9D](<Digital/AU Optronics/AUO122C/52AB56B29C9D>) |
| AU Optronics     | AUO122C | B133XW01 V2      | 1366x768  | 13.0 | 2008 | [CF91FBD2C8B4](<Digital/AU Optronics/AUO122C/CF91FBD2C8B4>) |
| AU Optronics     | AUO122C | B133XTF01        | 1366x768  | 13.0 |      | [A9EE1A8F739C](<Digital/AU Optronics/AUO122C/A9EE1A8F739C>) |
| AU Optronics     | AUO122D | B133HAK01.2      | 1920x1080 | 13.2 | 2016 | [C0CD610E2616](<Digital/AU Optronics/AUO122D/C0CD610E2616>) |
| AU Optronics     | AUO122D | B133HTN01.2      | 1920x1080 | 13.2 | 2013 | [E3E739DA41C2](<Digital/AU Optronics/AUO122D/E3E739DA41C2>) |
| AU Optronics     | AUO1236 | 564RX            | 2560x1440 | 13.9 | 2016 | [1F2AB7500645](<Digital/AU Optronics/AUO1236/1F2AB7500645>) |
| AU Optronics     | AUO123B |                  | 3840x2160 | 13.9 | 2018 | [324601DBA778](<Digital/AU Optronics/AUO123B/324601DBA778>) |
| AU Optronics     | AUO123C |                  | 1366x768  | 13.9 | 2015 | [CE086167FDAC](<Digital/AU Optronics/AUO123C/CE086167FDAC>) |
| AU Optronics     | AUO123C | 4D3YR            | 1366x768  | 13.9 | 2013 | [12F93FA07202](<Digital/AU Optronics/AUO123C/12F93FA07202>) |
| AU Optronics     | AUO123D | B140HTN01.2      | 1920x1080 | 13.9 | 2014 | [563D7381A410](<Digital/AU Optronics/AUO123D/563D7381A410>) |
| AU Optronics     | AUO123D |                  | 1920x1080 | 13.9 | 2013 | [109319C7DE3E](<Digital/AU Optronics/AUO123D/109319C7DE3E>) |
| AU Optronics     | AUO123D |                  | 1920x1080 | 13.9 | 2012 | [08368AF53CF1](<Digital/AU Optronics/AUO123D/08368AF53CF1>) |
| AU Optronics     | AUO123E |                  | 1600x900  | 13.9 | 2009 | [E9C51B5CC7C9](<Digital/AU Optronics/AUO123E/E9C51B5CC7C9>) |
| AU Optronics     | AUO1244 | FW579 (7DMn      | 1280x800  | 14.0 | 2006 | [6F39D6768DF1](<Digital/AU Optronics/AUO1244/6F39D6768DF1>) |
| AU Optronics     | AUO1244 | FD801            | 1280x800  | 15.1 |      | [992C3DF7186F](<Digital/AU Optronics/AUO1244/992C3DF7186F>) |
| AU Optronics     | AUO1247 | B141PW01 V2      | 1440x900  | 14.0 |      | [5FB31EA61619](<Digital/AU Optronics/AUO1247/5FB31EA61619>) |
| AU Optronics     | AUO125C |                  | 1366x768  | 11.6 | 2021 | [3F0566BBE877](<Digital/AU Optronics/AUO125C/3F0566BBE877>) |
| AU Optronics     | AUO125C | 9MH3J            | 1366x768  | 11.6 | 2018 | [03B81DB8969F](<Digital/AU Optronics/AUO125C/03B81DB8969F>) |
| AU Optronics     | AUO125C | T0HJY            | 1366x768  | 11.6 | 2017 | [99F7602DBC94](<Digital/AU Optronics/AUO125C/99F7602DBC94>) |
| AU Optronics     | AUO125C |                  | 1366x768  | 11.6 | 2016 | [6ADE20E38AA6](<Digital/AU Optronics/AUO125C/6ADE20E38AA6>) |
| AU Optronics     | AUO1296 | B160QAN02.M      | 2560x1600 | 15.9 | 2020 | [2D93565F9CA1](<Digital/AU Optronics/AUO1296/2D93565F9CA1>) |
| AU Optronics     | AUO129B | TJ6VM            | 3840x2160 | 17.1 | 2015 | [265D3B806ED5](<Digital/AU Optronics/AUO129B/265D3B806ED5>) |
| AU Optronics     | AUO129D | B173HAN01.2      | 1920x1080 | 17.1 | 2016 | [367E0BB36DD6](<Digital/AU Optronics/AUO129D/367E0BB36DD6>) |
| AU Optronics     | AUO129E |                  | 1600x900  | 17.1 | 2011 | [75F811F382B8](<Digital/AU Optronics/AUO129E/75F811F382B8>) |
| AU Optronics     | AUO129E |                  | 1600x900  | 17.1 | 2010 | [A8E1841ABC8B](<Digital/AU Optronics/AUO129E/A8E1841ABC8B>) |
| AU Optronics     | AUO129E | B173RW01 V2      | 1600x900  | 17.1 | 2009 | [8D58BC932D22](<Digital/AU Optronics/AUO129E/8D58BC932D22>) |
| AU Optronics     | AUO12D1 | B101AW01 V2      | 1024x576  | 10.1 | 2008 | [F24AB1060F2A](<Digital/AU Optronics/AUO12D1/F24AB1060F2A>) |
| AU Optronics     | AUO12D4 | B101EAN01.2      | 1280x800  | 10.3 | 2013 | [36AFE1317520](<Digital/AU Optronics/AUO12D4/36AFE1317520>) |
| AU Optronics     | AUO12EC |                  | 1366x768  | 15.3 | 2013 | [7963B10B703B](<Digital/AU Optronics/AUO12EC/7963B10B703B>) |
| AU Optronics     | AUO12EC | B156XW01 V2      | 1366x768  | 15.3 | 2008 | [31D403CA564A](<Digital/AU Optronics/AUO12EC/31D403CA564A>) |
| AU Optronics     | AUO12ED | B156HAN01.2      | 1920x1080 | 15.3 | 2012 | [62F95FF69997](<Digital/AU Optronics/AUO12ED/62F95FF69997>) |
| AU Optronics     | AUO132C | B133XTN01.3      | 1366x768  | 13.0 | 2014 | [C086BC4D2430](<Digital/AU Optronics/AUO132C/C086BC4D2430>) |
| AU Optronics     | AUO132C | B133XTF01.3      | 1366x768  | 13.0 | 2012 | [4977213E56DF](<Digital/AU Optronics/AUO132C/4977213E56DF>) |
| AU Optronics     | AUO132C |                  | 1366x768  | 13.0 | 2008 | [BB2DA15A9775](<Digital/AU Optronics/AUO132C/BB2DA15A9775>) |
| AU Optronics     | AUO1336 | B140QAN01.3      | 2560x1440 | 13.9 | 2016 | [303CF288E687](<Digital/AU Optronics/AUO1336/303CF288E687>) |
| AU Optronics     | AUO133B | B140ZAN01.3      | 3840x2160 | 13.9 | 2018 | [9EF5B13ACC8E](<Digital/AU Optronics/AUO133B/9EF5B13ACC8E>) |
| AU Optronics     | AUO133C | 6V83Y            | 1366x768  | 13.9 | 2014 | [218FD087DF58](<Digital/AU Optronics/AUO133C/218FD087DF58>) |
| AU Optronics     | AUO133C | B140XTN01.3      | 1366x768  | 13.9 | 2009 | [DA7BF6BF87DB](<Digital/AU Optronics/AUO133C/DA7BF6BF87DB>) |
| AU Optronics     | AUO133D | 8CVCF            | 1920x1080 | 13.9 | 2017 | [B146241C1880](<Digital/AU Optronics/AUO133D/B146241C1880>) |
| AU Optronics     | AUO133D | B140HAN01.3      | 1920x1080 | 13.9 | 2015 | [60D72F797D9A](<Digital/AU Optronics/AUO133D/60D72F797D9A>) |
| AU Optronics     | AUO133D |                  | 1920x1080 | 13.9 | 2014 | [84911403AA39](<Digital/AU Optronics/AUO133D/84911403AA39>) |
| AU Optronics     | AUO133D | M1WHV            | 1920x1080 | 13.9 | 2013 | [2D87F4C54500](<Digital/AU Optronics/AUO133D/2D87F4C54500>) |
| AU Optronics     | AUO1344 | B141EW01 V3      | 1280x800  | 14.0 |      | [E8CACA88036C](<Digital/AU Optronics/AUO1344/E8CACA88036C>) |
| AU Optronics     | AUO1347 | GR584 (8CLl      | 1440x900  | 14.0 | 2006 | [46A94E853C69](<Digital/AU Optronics/AUO1347/46A94E853C69>) |
| AU Optronics     | AUO135C |                  | 1366x768  | 11.6 | 2016 | [FE144EA1391A](<Digital/AU Optronics/AUO135C/FE144EA1391A>) |
| AU Optronics     | AUO1396 | 48TD4            | 2560x1440 | 17.1 | 2018 | [ECE3113BFD5A](<Digital/AU Optronics/AUO1396/ECE3113BFD5A>) |
| AU Optronics     | AUO1399 | CDJJ8            | 1366x768  | 13.9 | 2021 | [30568670C8B6](<Digital/AU Optronics/AUO1399/30568670C8B6>) |
| AU Optronics     | AUO139D | 6HK8X            | 1920x1080 | 17.1 | 2019 | [41EB68CE7FD0](<Digital/AU Optronics/AUO139D/41EB68CE7FD0>) |
| AU Optronics     | AUO139D | W27J0            | 1920x1080 | 17.1 | 2018 | [12ECBC0469F2](<Digital/AU Optronics/AUO139D/12ECBC0469F2>) |
| AU Optronics     | AUO139D | MWY7K            | 1920x1080 | 17.1 | 2017 | [06462EC42339](<Digital/AU Optronics/AUO139D/06462EC42339>) |
| AU Optronics     | AUO139D | B173HAN01.3      | 1920x1080 | 17.1 | 2015 | [BBB88A7E9373](<Digital/AU Optronics/AUO139D/BBB88A7E9373>) |
| AU Optronics     | AUO139E | B173RTN01.3      | 1600x900  | 17.1 | 2014 | [23B3D5D783F1](<Digital/AU Optronics/AUO139E/23B3D5D783F1>) |
| AU Optronics     | AUO139E | B173RTN01.3      | 1600x900  | 17.1 | 2012 | [0AD2C121F5B0](<Digital/AU Optronics/AUO139E/0AD2C121F5B0>) |
| AU Optronics     | AUO139E |                  | 1600x900  | 17.1 | 2011 | [31D7B01C95D9](<Digital/AU Optronics/AUO139E/31D7B01C95D9>) |
| AU Optronics     | AUO139E | B173RW01 V3      | 1600x900  | 17.1 | 2010 | [2F895156DD41](<Digital/AU Optronics/AUO139E/2F895156DD41>) |
| AU Optronics     | AUO139E | B173RW01 V3      | 1600x900  | 17.1 | 2009 | [27C5D04CA16B](<Digital/AU Optronics/AUO139E/27C5D04CA16B>) |
| AU Optronics     | AUO13B2 | 8C5MG            | 2560x1600 | 14.0 | 2024 | [874EAA0044DD](<Digital/AU Optronics/AUO13B2/874EAA0044DD>) |
| AU Optronics     | AUO13C2 | B089AW01 V3      | 1024x600  | 9.0  | 2008 | [5868A67F2C0B](<Digital/AU Optronics/AUO13C2/5868A67F2C0B>) |
| AU Optronics     | AUO13D1 | B101AW01 V3      | 1024x576  | 10.1 | 2008 | [9231CFD69572](<Digital/AU Optronics/AUO13D1/9231CFD69572>) |
| AU Optronics     | AUO13EC | VJHRG            | 1366x768  | 15.3 | 2015 | [A2D54F23D8C2](<Digital/AU Optronics/AUO13EC/A2D54F23D8C2>) |
| AU Optronics     | AUO13ED |                  | 1920x1080 | 15.3 | 2008 | [519F5D1E1BF8](<Digital/AU Optronics/AUO13ED/519F5D1E1BF8>) |
| AU Optronics     | AUO13EE | G370R            | 1600x900  | 15.3 | 2008 | [3B559811A16E](<Digital/AU Optronics/AUO13EE/3B559811A16E>) |
| AU Optronics     | AUO1424 | MT679            | 1280x800  | 13.4 | 2008 | [B4AC5DD8DFA8](<Digital/AU Optronics/AUO1424/B4AC5DD8DFA8>) |
| AU Optronics     | AUO1424 | DW909 *:GPr      | 1280x800  | 13.4 | 2007 | [709FBE447288](<Digital/AU Optronics/AUO1424/709FBE447288>) |
| AU Optronics     | AUO1424 |                  | 1280x800  | 13.4 | 2006 | [2D07600CA91B](<Digital/AU Optronics/AUO1424/2D07600CA91B>) |
| AU Optronics     | AUO142D | 6MFCT            | 1920x1080 | 13.2 | 2017 | [5BB1EA783F56](<Digital/AU Optronics/AUO142D/5BB1EA783F56>) |
| AU Optronics     | AUO142D | B133HTN01.4      | 1920x1080 | 13.2 | 2016 | [63E5A18DE6BC](<Digital/AU Optronics/AUO142D/63E5A18DE6BC>) |
| AU Optronics     | AUO143B | VJ37W            | 3840x2160 | 13.9 | 2019 | [C844D83788AC](<Digital/AU Optronics/AUO143B/C844D83788AC>) |
| AU Optronics     | AUO143C |                  | 1366x768  | 13.9 | 2009 | [4A8F88478895](<Digital/AU Optronics/AUO143C/4A8F88478895>) |
| AU Optronics     | AUO143D | B140HAN01.4      | 1920x1080 | 13.9 | 2014 | [326222F1F4B9](<Digital/AU Optronics/AUO143D/326222F1F4B9>) |
| AU Optronics     | AUO143D | B140HTN01.4      | 1920x1080 | 13.9 | 2013 | [ACAB08DDF772](<Digital/AU Optronics/AUO143D/ACAB08DDF772>) |
| AU Optronics     | AUO1444 | XU295            | 1280x800  | 14.0 |      | [F4ACA7093C1F](<Digital/AU Optronics/AUO1444/F4ACA7093C1F>) |
| AU Optronics     | AUO1447 | U804G )9FOo      | 1440x900  | 14.0 | 2006 | [358984D42C30](<Digital/AU Optronics/AUO1447/358984D42C30>) |
| AU Optronics     | AUO145C |                  | 1366x768  | 11.6 | 2017 | [96357B7FE2FF](<Digital/AU Optronics/AUO145C/96357B7FE2FF>) |
| AU Optronics     | AUO145C |                  | 1366x768  | 11.6 | 2016 | [117801EB052A](<Digital/AU Optronics/AUO145C/117801EB052A>) |
| AU Optronics     | AUO1474 | CD514 0AMWx      | 1280x800  | 15.4 |      | [0676AE4A9E74](<Digital/AU Optronics/AUO1474/0676AE4A9E74>) |
| AU Optronics     | AUO1496 | B173QTN01.4      | 2560x1440 | 17.1 | 2016 | [F40764034490](<Digital/AU Optronics/AUO1496/F40764034490>) |
| AU Optronics     | AUO1496 | JYWWF            | 2560x1440 | 17.1 |      | [6B99B0883D78](<Digital/AU Optronics/AUO1496/6B99B0883D78>) |
| AU Optronics     | AUO1499 | B140XTN07.2      | 1366x768  | 13.9 | 2020 | [58DD09238F1C](<Digital/AU Optronics/AUO1499/58DD09238F1C>) |
| AU Optronics     | AUO149B |                  | 3840x2160 | 17.1 | 2017 | [454046FC0244](<Digital/AU Optronics/AUO149B/454046FC0244>) |
| AU Optronics     | AUO149D |                  | 1920x1080 | 17.1 | 2016 | [C818370CC028](<Digital/AU Optronics/AUO149D/C818370CC028>) |
| AU Optronics     | AUO149D | B173HW01 V4      | 1920x1080 | 17.1 | 2009 | [4DEE71E19E78](<Digital/AU Optronics/AUO149D/4DEE71E19E78>) |
| AU Optronics     | AUO149E |                  | 1600x900  | 17.1 | 2012 | [293B8D2FD303](<Digital/AU Optronics/AUO149E/293B8D2FD303>) |
| AU Optronics     | AUO149E | NRFX3            | 1600x900  | 17.1 | 2011 | [1304D5B28F59](<Digital/AU Optronics/AUO149E/1304D5B28F59>) |
| AU Optronics     | AUO14D4 |                  | 1280x800  | 10.3 | 2014 | [3A111CE66907](<Digital/AU Optronics/AUO14D4/3A111CE66907>) |
| AU Optronics     | AUO1514 |                  | 1280x800  | 12.0 | 2005 | [EF3CB480BD81](<Digital/AU Optronics/AUO1514/EF3CB480BD81>) |
| AU Optronics     | AUO152C | B133XTN01.5      | 1366x768  | 13.0 | 2012 | [27F60BCF1051](<Digital/AU Optronics/AUO152C/27F60BCF1051>) |
| AU Optronics     | AUO1533 | B140EW01 V5      | 1280x768  | 15.2 |      | [16441586BE26](<Digital/AU Optronics/AUO1533/16441586BE26>) |
| AU Optronics     | AUO1536 | B140QAN01        | 2560x1440 | 13.9 |      | [4CDB17DA95AD](<Digital/AU Optronics/AUO1536/4CDB17DA95AD>) |
| AU Optronics     | AUO155C |                  | 1366x768  | 11.6 | 2017 | [804A215783F5](<Digital/AU Optronics/AUO155C/804A215783F5>) |
| AU Optronics     | AUO1596 | 2JVM6            | 2560x1440 | 17.1 | 2017 | [2CB4F5ECFC9F](<Digital/AU Optronics/AUO1596/2CB4F5ECFC9F>) |
| AU Optronics     | AUO159D | B173HW01 V5      | 1920x1080 | 17.1 | 2011 | [33C7EE4DAD20](<Digital/AU Optronics/AUO159D/33C7EE4DAD20>) |
| AU Optronics     | AUO159D | B173HW01 V5      | 1920x1080 | 17.1 | 2010 | [7F5E4B6F8279](<Digital/AU Optronics/AUO159D/7F5E4B6F8279>) |
| AU Optronics     | AUO159D |                  | 1920x1080 | 17.1 | 2009 | [3760476ADEF1](<Digital/AU Optronics/AUO159D/3760476ADEF1>) |
| AU Optronics     | AUO159E |                  | 1600x900  | 17.1 | 2012 | [8630F19454BD](<Digital/AU Optronics/AUO159E/8630F19454BD>) |
| AU Optronics     | AUO159E | DYMX0            | 1600x900  | 17.1 | 2011 | [779C57B0F484](<Digital/AU Optronics/AUO159E/779C57B0F484>) |
| AU Optronics     | AUO15A7 | B140UAN05.1      | 1920x1200 | 14.0 | 2022 | [98D033712BA4](<Digital/AU Optronics/AUO15A7/98D033712BA4>) |
| AU Optronics     | AUO15ED | B156HW01 V5      | 1920x1080 | 15.3 | 2008 | [4A5C7F54C66F](<Digital/AU Optronics/AUO15ED/4A5C7F54C66F>) |
| AU Optronics     | AUO162C | 2C7YD            | 1366x768  | 13.0 | 2018 | [47E6ACBCA311](<Digital/AU Optronics/AUO162C/47E6ACBCA311>) |
| AU Optronics     | AUO162C |                  | 1366x768  | 13.0 | 2015 | [C3A72ADB8F8B](<Digital/AU Optronics/AUO162C/C3A72ADB8F8B>) |
| AU Optronics     | AUO162C | B133XTN01.6      | 1366x768  | 13.0 | 2014 | [1DF03A82F5B3](<Digital/AU Optronics/AUO162C/1DF03A82F5B3>) |
| AU Optronics     | AUO162C | B133XTN01        | 1366x768  | 13.0 |      | [78DC479EDD35](<Digital/AU Optronics/AUO162C/78DC479EDD35>) |
| AU Optronics     | AUO163C | B140XW01 V6      | 1366x768  | 13.9 | 2009 | [CAC26223D044](<Digital/AU Optronics/AUO163C/CAC26223D044>) |
| AU Optronics     | AUO163D | B140HTN01.6      | 1920x1080 | 13.9 | 2013 | [7F224FDD6849](<Digital/AU Optronics/AUO163D/7F224FDD6849>) |
| AU Optronics     | AUO168E |                  | 3840x2160 | 17.1 | 2019 | [7921EC2166E5](<Digital/AU Optronics/AUO168E/7921EC2166E5>) |
| AU Optronics     | AUO169D |                  | 1920x1080 | 17.1 | 2017 | [DFB6B6BC2D5C](<Digital/AU Optronics/AUO169D/DFB6B6BC2D5C>) |
| AU Optronics     | AUO1718 |                  | 3840x2160 | 15.3 | 2019 | [8F005B1B0CAE](<Digital/AU Optronics/AUO1718/8F005B1B0CAE>) |
| AU Optronics     | AUO172C | B133XW01 V7      | 1366x768  | 13.0 | 2008 | [5296BA00EBAC](<Digital/AU Optronics/AUO172C/5296BA00EBAC>) |
| AU Optronics     | AUO173D | B140HAN01.7      | 1920x1080 | 13.9 | 2014 | [732BCCC7E7A9](<Digital/AU Optronics/AUO173D/732BCCC7E7A9>) |
| AU Optronics     | AUO1751 | B150XG01V7       | 1024x768  | 14.9 |      | [FEC10DBDE98D](<Digital/AU Optronics/AUO1751/FEC10DBDE98D>) |
| AU Optronics     | AUO177B | JT331 *:EMl      | 1680x1050 | 15.4 | 2007 | [46E9913F2177](<Digital/AU Optronics/AUO177B/46E9913F2177>) |
| AU Optronics     | AUO179D | B173HAN01.7      | 1920x1080 | 17.1 | 2017 | [23D6D3AC947D](<Digital/AU Optronics/AUO179D/23D6D3AC947D>) |
| AU Optronics     | AUO17ED | KYYVK            | 1920x1080 | 15.3 | 2010 | [B462AD5953D0](<Digital/AU Optronics/AUO17ED/B462AD5953D0>) |
| AU Optronics     | AUO183C |                  | 1366x768  | 13.9 | 2011 | [207B9E4E17B8](<Digital/AU Optronics/AUO183C/207B9E4E17B8>) |
| AU Optronics     | AUO183C | B140XW01 V8      | 1366x768  | 13.9 | 2009 | [66CE90ACF0E8](<Digital/AU Optronics/AUO183C/66CE90ACF0E8>) |
| AU Optronics     | AUO183D | B140HAN01.8      | 1920x1080 | 13.9 | 2014 | [DA8AC6AFB31D](<Digital/AU Optronics/AUO183D/DA8AC6AFB31D>) |
| AU Optronics     | AUO1851 | B150XG01V8       | 1024x768  | 14.9 |      | [7C509EFC123F](<Digital/AU Optronics/AUO1851/7C509EFC123F>) |
| AU Optronics     | AUO1874 | B154EW01 V8      | 1280x800  | 15.4 |      | [0BDC0161E1D4](<Digital/AU Optronics/AUO1874/0BDC0161E1D4>) |
| AU Optronics     | AUO187B | JT331            | 1680x1050 | 15.4 | 2007 | [86FCC5A53A0F](<Digital/AU Optronics/AUO187B/86FCC5A53A0F>) |
| AU Optronics     | AUO18A7 | VYVP0            | 1920x1200 | 15.9 | 2022 | [9B0883AE2660](<Digital/AU Optronics/AUO18A7/9B0883AE2660>) |
| AU Optronics     | AUO18D4 |                  | 1280x800  | 10.3 | 2013 | [20D085AEC72C](<Digital/AU Optronics/AUO18D4/20D085AEC72C>) |
| AU Optronics     | AUO1918 |                  | 3840x2160 | 15.3 | 2019 | [42647BC5916B](<Digital/AU Optronics/AUO1918/42647BC5916B>) |
| AU Optronics     | AUO193C |                  | 1366x768  | 13.9 | 2011 | [A4F4C2F186A0](<Digital/AU Optronics/AUO193C/A4F4C2F186A0>) |
| AU Optronics     | AUO193C | B140XW01 V9      | 1366x768  | 13.9 | 2009 | [23B3C5D13CA4](<Digital/AU Optronics/AUO193C/23B3C5D13CA4>) |
| AU Optronics     | AUO1974 | B154EW01 V9      | 1280x800  | 15.4 |      | [5F96C8435218](<Digital/AU Optronics/AUO1974/5F96C8435218>) |
| AU Optronics     | AUO197B | B154SW01 V9      | 1680x1050 | 15.4 | 2007 | [21C92ED0DB78](<Digital/AU Optronics/AUO197B/21C92ED0DB78>) |
| AU Optronics     | AUO1999 |                  | 1366x768  | 13.9 | 2020 | [56CFC521F5E9](<Digital/AU Optronics/AUO1999/56CFC521F5E9>) |
| AU Optronics     | AUO19AC | B160QAN03.R      | 2560x1600 | 15.9 | 2023 | [99F9A2D550ED](<Digital/AU Optronics/AUO19AC/99F9A2D550ED>) |
| AU Optronics     | AUO1A87 |                  | 1920x1080 | 13.2 | 2020 | [0E2B72B707C6](<Digital/AU Optronics/AUO1A87/0E2B72B707C6>) |
| AU Optronics     | AUO1A94 | B139KAN01.0      | 3300x2200 | 13.9 | 2019 | [2E1855DC851C](<Digital/AU Optronics/AUO1A94/2E1855DC851C>) |
| AU Optronics     | AUO1AA7 |                  | 1920x1200 | 15.9 | 2022 | [4DA548C962D4](<Digital/AU Optronics/AUO1AA7/4DA548C962D4>) |
| AU Optronics     | AUO1AB1 | V8C3R            | 1920x1200 | 14.0 | 2024 | [E09719E7E0A6](<Digital/AU Optronics/AUO1AB1/E09719E7E0A6>) |
| AU Optronics     | AUO1AD8 |                  | 1920x1200 | 10.3 | 2013 | [7B9EF57DF4C3](<Digital/AU Optronics/AUO1AD8/7B9EF57DF4C3>) |
| AU Optronics     | AUO1B3C | B140XW01 VB      | 1366x768  | 13.9 | 2009 | [B02221DA4D4E](<Digital/AU Optronics/AUO1B3C/B02221DA4D4E>) |
| AU Optronics     | AUO1B3D | Y753W            | 1920x1080 | 13.9 | 2015 | [78094B108194](<Digital/AU Optronics/AUO1B3D/78094B108194>) |
| AU Optronics     | AUO1B3D | B140HTN01.B      | 1920x1080 | 13.9 | 2014 | [309F9AEF8378](<Digital/AU Optronics/AUO1B3D/309F9AEF8378>) |
| AU Optronics     | AUO1B7B | B154SW01 VB      | 1680x1050 | 15.4 | 2007 | [0A2150F1BB9A](<Digital/AU Optronics/AUO1B7B/0A2150F1BB9A>) |
| AU Optronics     | AUO1BD8 |                  | 1920x1200 | 10.3 | 2013 | [32277A3855BF](<Digital/AU Optronics/AUO1BD8/32277A3855BF>) |
| AU Optronics     | AUO1C3C | B140XW01 VC      | 1366x768  | 13.9 | 2016 | [727188A1FFC6](<Digital/AU Optronics/AUO1C3C/727188A1FFC6>) |
| AU Optronics     | AUO1C3D | B140HTN01.C      | 1920x1080 | 13.9 | 2014 | [8E280E0AE5CC](<Digital/AU Optronics/AUO1C3D/8E280E0AE5CC>) |
| AU Optronics     | AUO1C74 | FF059 0AMWx      | 1280x800  | 15.4 |      | [C784301B17EA](<Digital/AU Optronics/AUO1C74/C784301B17EA>) |
| AU Optronics     | AUO1CA5 | B160QAN02.3      | 2560x1600 | 15.9 | 2022 | [94EEEEF53A67](<Digital/AU Optronics/AUO1CA5/94EEEEF53A67>) |
| AU Optronics     | AUO1CA7 |                  | 2560x1600 | 15.9 | 2022 | [C9BF9F4F707C](<Digital/AU Optronics/AUO1CA7/C9BF9F4F707C>) |
| AU Optronics     | AUO1CB0 |                  | 1920x1200 | 15.9 | 2024 | [5FCB7869F6C6](<Digital/AU Optronics/AUO1CB0/5FCB7869F6C6>) |
| AU Optronics     | AUO1D3D | B140HTN01.D      | 1920x1080 | 13.9 | 2015 | [9C3A799E3965](<Digital/AU Optronics/AUO1D3D/9C3A799E3965>) |
| AU Optronics     | AUO1D8F | B133UAN01.0      | 1920x1200 | 13.4 | 2019 | [F654A6964DEB](<Digital/AU Optronics/AUO1D8F/F654A6964DEB>) |
| AU Optronics     | AUO1DB0 |                  | 1920x1200 | 14.0 | 2023 | [DD24F1EAFD6E](<Digital/AU Optronics/AUO1DB0/DD24F1EAFD6E>) |
| AU Optronics     | AUO1E3D |                  | 1920x1080 | 13.9 | 2016 | [7ECDE1E311F7](<Digital/AU Optronics/AUO1E3D/7ECDE1E311F7>) |
| AU Optronics     | AUO1E3D | B140HTN01.E      | 1920x1080 | 13.9 | 2015 | [AFB1132DF54F](<Digital/AU Optronics/AUO1E3D/AFB1132DF54F>) |
| AU Optronics     | AUO1E9B |                  | 1920x1200 | 13.4 | 2021 | [0B65659E6547](<Digital/AU Optronics/AUO1E9B/0B65659E6547>) |
| AU Optronics     | AUO1EAC |                  | 1920x1200 | 14.5 | 2023 | [F07DC8A0F417](<Digital/AU Optronics/AUO1EAC/F07DC8A0F417>) |
| AU Optronics     | AUO1F3D | B140HTN01.F      | 1920x1080 | 13.9 | 2015 | [F512894873C8](<Digital/AU Optronics/AUO1F3D/F512894873C8>) |
| AU Optronics     | AUO1F92 | M5DY2            | 1920x1080 | 15.3 | 2020 | [3AEEA5AC0C9B](<Digital/AU Optronics/AUO1F92/3AEEA5AC0C9B>) |
| AU Optronics     | AUO2026 | B133QAN02.0      | 2560x1600 | 13.4 | 2018 | [B7CBDA80937A](<Digital/AU Optronics/AUO2026/B7CBDA80937A>) |
| AU Optronics     | AUO202B |                  | 3840x2160 | 13.2 | 2017 | [B2F2BA4E91FE](<Digital/AU Optronics/AUO202B/B2F2BA4E91FE>) |
| AU Optronics     | AUO202C | B133XW02 V0      | 1366x768  | 13.0 | 2008 | [0331FD1FC880](<Digital/AU Optronics/AUO202C/0331FD1FC880>) |
| AU Optronics     | AUO202D | D2TNH            | 1920x1080 | 13.2 | 2018 | [B9CEE0C1D054](<Digital/AU Optronics/AUO202D/B9CEE0C1D054>) |
| AU Optronics     | AUO202D | B133HAN02.0      | 1920x1080 | 13.2 | 2012 | [BB4728F53E08](<Digital/AU Optronics/AUO202D/BB4728F53E08>) |
| AU Optronics     | AUO2036 | B140QAN02.0      | 2560x1440 | 13.9 | 2017 | [16F41B2CA9F5](<Digital/AU Optronics/AUO2036/16F41B2CA9F5>) |
| AU Optronics     | AUO203C |                  | 1366x768  | 13.9 | 2019 | [23163A489FB1](<Digital/AU Optronics/AUO203C/23163A489FB1>) |
| AU Optronics     | AUO203C |                  | 1366x768  | 13.9 | 2018 | [B0D5B4875255](<Digital/AU Optronics/AUO203C/B0D5B4875255>) |
| AU Optronics     | AUO203C |                  | 1366x768  | 13.9 | 2011 | [0250C1896648](<Digital/AU Optronics/AUO203C/0250C1896648>) |
| AU Optronics     | AUO203C | B140XW02 V0      | 1366x768  | 13.9 | 2008 | [2322FD20631E](<Digital/AU Optronics/AUO203C/2322FD20631E>) |
| AU Optronics     | AUO203C | 9TMDG            | 1366x768  | 13.9 |      | [1B8F7606109E](<Digital/AU Optronics/AUO203C/1B8F7606109E>) |
| AU Optronics     | AUO203D | B140HTN02.0      | 1920x1080 | 13.9 | 2019 | [83A2E28B89D0](<Digital/AU Optronics/AUO203D/83A2E28B89D0>) |
| AU Optronics     | AUO203D |                  | 1920x1080 | 13.9 | 2018 | [29091B1010BE](<Digital/AU Optronics/AUO203D/29091B1010BE>) |
| AU Optronics     | AUO203D | B140HAK02.0      | 1920x1080 | 13.9 | 2017 | [BE8419D68882](<Digital/AU Optronics/AUO203D/BE8419D68882>) |
| AU Optronics     | AUO203D | B140HAT02.0      | 1920x1080 | 13.9 | 2015 | [068123586688](<Digital/AU Optronics/AUO203D/068123586688>) |
| AU Optronics     | AUO203E | B140RW02 V0      | 1600x900  | 13.9 | 2010 | [B0C70561F414](<Digital/AU Optronics/AUO203E/B0C70561F414>) |
| AU Optronics     | AUO203E | B140RW02 V0      | 1600x900  | 13.9 | 2009 | [4FCC0E83D008](<Digital/AU Optronics/AUO203E/4FCC0E83D008>) |
| AU Optronics     | AUO2052 | B116AW02 V0      | 1024x600  | 11.6 | 2009 | [BC8095DFECAE](<Digital/AU Optronics/AUO2052/BC8095DFECAE>) |
| AU Optronics     | AUO205C |                  | 1366x768  | 11.6 | 2019 | [4B5ABEB587F7](<Digital/AU Optronics/AUO205C/4B5ABEB587F7>) |
| AU Optronics     | AUO205C | B116XAN02.0      | 1366x768  | 11.6 | 2012 | [DC012098A317](<Digital/AU Optronics/AUO205C/DC012098A317>) |
| AU Optronics     | AUO205C | B116XW02 V0      | 1366x768  | 11.6 | 2011 | [B36E03B7C593](<Digital/AU Optronics/AUO205C/B36E03B7C593>) |
| AU Optronics     | AUO205C |                  | 1366x768  | 11.6 | 2008 | [3AD39C2CB51B](<Digital/AU Optronics/AUO205C/3AD39C2CB51B>) |
| AU Optronics     | AUO206C | M6F9D            | 1366x768  | 12.7 | 2013 | [A69BCABB2646](<Digital/AU Optronics/AUO206C/A69BCABB2646>) |
| AU Optronics     | AUO206C |                  | 1366x768  | 12.7 | 2012 | [9BA00E3B28D8](<Digital/AU Optronics/AUO206C/9BA00E3B28D8>) |
| AU Optronics     | AUO206C |                  | 1366x768  | 12.7 | 2010 | [2D63DC154B41](<Digital/AU Optronics/AUO206C/2D63DC154B41>) |
| AU Optronics     | AUO206D |                  | 1920x1080 | 12.7 | 2015 | [64196F93C198](<Digital/AU Optronics/AUO206D/64196F93C198>) |
| AU Optronics     | AUO206D | FDM42            | 1920x1080 | 12.7 | 2014 | [E394DA23045F](<Digital/AU Optronics/AUO206D/E394DA23045F>) |
| AU Optronics     | AUO2074 | B154EW02 V0      | 1280x800  | 15.4 | 2006 | [6E9658078AA4](<Digital/AU Optronics/AUO2074/6E9658078AA4>) |
| AU Optronics     | AUO2074 | B154EW02 V0      | 1280x800  | 15.4 |      | [68E8182103E9](<Digital/AU Optronics/AUO2074/68E8182103E9>) |
| AU Optronics     | AUO2077 | W659G &5@Hf      | 1440x900  | 15.4 | 2008 | [32ACFF215B78](<Digital/AU Optronics/AUO2077/32ACFF215B78>) |
| AU Optronics     | AUO2077 |                  | 1440x900  | 15.4 | 2006 | [03A4AE3068B7](<Digital/AU Optronics/AUO2077/03A4AE3068B7>) |
| AU Optronics     | AUO2088 | B170UW02 V0      | 1920x1200 | 17.2 | 2007 | [DF3BDD1741B9](<Digital/AU Optronics/AUO2088/DF3BDD1741B9>) |
| AU Optronics     | AUO208D | B140HTN02.1      | 1920x1080 | 13.9 | 2019 | [A0A5851C2AD8](<Digital/AU Optronics/AUO208D/A0A5851C2AD8>) |
| AU Optronics     | AUO209D | B173HW02 V0      | 1920x1080 | 17.1 | 2011 | [DEFFB87123F4](<Digital/AU Optronics/AUO209D/DEFFB87123F4>) |
| AU Optronics     | AUO20A7 | B140UAN04.4      | 1920x1200 | 14.0 | 2022 | [80CA958EB9C6](<Digital/AU Optronics/AUO20A7/80CA958EB9C6>) |
| AU Optronics     | AUO20D2 | B101AW02 V0      | 1024x600  | 10.1 | 2008 | [44427A32B938](<Digital/AU Optronics/AUO20D2/44427A32B938>) |
| AU Optronics     | AUO20D5 | B101EW02 V0      | 1280x720  | 10.1 | 2009 | [A26680A3695C](<Digital/AU Optronics/AUO20D5/A26680A3695C>) |
| AU Optronics     | AUO20EB | G3596            | 3840x2160 | 15.7 | 2016 | [003EEBBCE97E](<Digital/AU Optronics/AUO20EB/003EEBBCE97E>) |
| AU Optronics     | AUO20EC |                  | 1366x768  | 15.3 | 2018 | [09B28FCE3F19](<Digital/AU Optronics/AUO20EC/09B28FCE3F19>) |
| AU Optronics     | AUO20EC | B156XTN02.0      | 1366x768  | 15.3 | 2013 | [2079FD22EC14](<Digital/AU Optronics/AUO20EC/2079FD22EC14>) |
| AU Optronics     | AUO20EC | P5CK7            | 1366x768  | 15.3 | 2011 | [1DD6105CE217](<Digital/AU Optronics/AUO20EC/1DD6105CE217>) |
| AU Optronics     | AUO20EC | F414J            | 1366x768  | 15.3 | 2008 | [0826D411B2D2](<Digital/AU Optronics/AUO20EC/0826D411B2D2>) |
| AU Optronics     | AUO20ED | B156HAN02.0      | 1920x1080 | 15.3 | 2018 | [2F2D34A18EF8](<Digital/AU Optronics/AUO20ED/2F2D34A18EF8>) |
| AU Optronics     | AUO20ED | B156HAK02.0      | 1920x1080 | 15.3 | 2017 | [52D103B3A939](<Digital/AU Optronics/AUO20ED/52D103B3A939>) |
| AU Optronics     | AUO20ED |                  | 1920x1080 | 15.3 | 2016 | [0C0B65657CF4](<Digital/AU Optronics/AUO20ED/0C0B65657CF4>) |
| AU Optronics     | AUO20ED |                  | 1920x1080 | 15.3 |      | [676CDB37F073](<Digital/AU Optronics/AUO20ED/676CDB37F073>) |
| AU Optronics     | AUO212B | 0NKNX            | 3840x2160 | 13.2 | 2017 | [889107CE257C](<Digital/AU Optronics/AUO212B/889107CE257C>) |
| AU Optronics     | AUO212C |                  | 1366x768  | 13.0 | 2015 | [A34D15D73517](<Digital/AU Optronics/AUO212C/A34D15D73517>) |
| AU Optronics     | AUO212C | B133XTN02.1      | 1366x768  | 13.0 | 2013 | [AE4D7E2307C1](<Digital/AU Optronics/AUO212C/AE4D7E2307C1>) |
| AU Optronics     | AUO212C | B133XW02 V1      | 1366x768  | 13.0 | 2008 | [11142ECFD3BF](<Digital/AU Optronics/AUO212C/11142ECFD3BF>) |
| AU Optronics     | AUO212D | HHYCY            | 1920x1080 | 13.2 | 2019 | [2BD6C57E1FDF](<Digital/AU Optronics/AUO212D/2BD6C57E1FDF>) |
| AU Optronics     | AUO212D | B133HAN02.1      | 1920x1080 | 13.2 | 2013 | [029A92C8ABDC](<Digital/AU Optronics/AUO212D/029A92C8ABDC>) |
| AU Optronics     | AUO213C | B140XTN02.1      | 1366x768  | 13.9 | 2011 | [4FB3C4159230](<Digital/AU Optronics/AUO213C/4FB3C4159230>) |
| AU Optronics     | AUO213C | TP3HR            | 1366x768  | 13.9 | 2009 | [05E6078817D4](<Digital/AU Optronics/AUO213C/05E6078817D4>) |
| AU Optronics     | AUO213C | B140XW02 V1      | 1366x768  | 13.9 | 2008 | [5BEEDB322AAA](<Digital/AU Optronics/AUO213C/5BEEDB322AAA>) |
| AU Optronics     | AUO213D |                  | 1920x1080 | 13.9 | 2018 | [C5162CD4D1F1](<Digital/AU Optronics/AUO213D/C5162CD4D1F1>) |
| AU Optronics     | AUO213D |                  | 1920x1080 | 13.9 | 2017 | [16419F50B7B4](<Digital/AU Optronics/AUO213D/16419F50B7B4>) |
| AU Optronics     | AUO213D | KJW6Y            | 1920x1080 | 13.9 | 2016 | [B3001554710F](<Digital/AU Optronics/AUO213D/B3001554710F>) |
| AU Optronics     | AUO213D |                  | 1920x1080 | 13.9 | 2015 | [80AE159B9A02](<Digital/AU Optronics/AUO213D/80AE159B9A02>) |
| AU Optronics     | AUO213E | V3YHF            | 1600x900  | 13.9 | 2011 | [50069ACEADCD](<Digital/AU Optronics/AUO213E/50069ACEADCD>) |
| AU Optronics     | AUO213E | B140RW02 V1      | 1600x900  | 13.9 | 2010 | [70CC44D94BF6](<Digital/AU Optronics/AUO213E/70CC44D94BF6>) |
| AU Optronics     | AUO2144 | B141EW02 V1      | 1280x800  | 14.0 |      | [93A407706055](<Digital/AU Optronics/AUO2144/93A407706055>) |
| AU Optronics     | AUO215C | B116XTN02.1      | 1366x768  | 11.6 | 2013 | [C0BD51934254](<Digital/AU Optronics/AUO215C/C0BD51934254>) |
| AU Optronics     | AUO215C | B116XW02 V1      | 1366x768  | 11.6 | 2009 | [5ED619B6A595](<Digital/AU Optronics/AUO215C/5ED619B6A595>) |
| AU Optronics     | AUO215C | B116XW02 V1      | 1366x768  | 11.6 | 2008 | [1087F1089FA0](<Digital/AU Optronics/AUO215C/1087F1089FA0>) |
| AU Optronics     | AUO2174 | B154EW02 V1      | 1280x800  | 15.4 |      | [9029BF84444E](<Digital/AU Optronics/AUO2174/9029BF84444E>) |
| AU Optronics     | AUO2177 | NY850            | 1440x900  | 15.4 | 2008 | [86AE06E3F5A8](<Digital/AU Optronics/AUO2177/86AE06E3F5A8>) |
| AU Optronics     | AUO219C | 8VRPM            | 1920x1200 | 15.9 | 2021 | [AC12AAFAE789](<Digital/AU Optronics/AUO219C/AC12AAFAE789>) |
| AU Optronics     | AUO219D | P9JNK            | 1920x1080 | 17.1 | 2013 | [C4DEC67153E2](<Digital/AU Optronics/AUO219D/C4DEC67153E2>) |
| AU Optronics     | AUO219D | B173HW02 V1      | 1920x1080 | 17.1 | 2012 | [6AE87C50B350](<Digital/AU Optronics/AUO219D/6AE87C50B350>) |
| AU Optronics     | AUO219D |                  | 1920x1080 | 17.1 | 2011 | [552D42BACC44](<Digital/AU Optronics/AUO219D/552D42BACC44>) |
| AU Optronics     | AUO219E |                  | 1600x900  | 17.1 | 2018 | [C294FC3210D5](<Digital/AU Optronics/AUO219E/C294FC3210D5>) |
| AU Optronics     | AUO219E | C00WX            | 1600x900  | 17.1 | 2016 | [D08CF3DE9565](<Digital/AU Optronics/AUO219E/D08CF3DE9565>) |
| AU Optronics     | AUO219E | B173RTN02.1      | 1600x900  | 17.1 | 2015 | [470693E137CF](<Digital/AU Optronics/AUO219E/470693E137CF>) |
| AU Optronics     | AUO21EB | B156ZAN02.1      | 3840x2160 | 15.7 | 2016 | [6E11567441F6](<Digital/AU Optronics/AUO21EB/6E11567441F6>) |
| AU Optronics     | AUO21EC | G156XTN02.1      | 1366x768  | 15.3 | 2018 | [A34568B92063](<Digital/AU Optronics/AUO21EC/A34568B92063>) |
| AU Optronics     | AUO21EC | B156XTN02.1      | 1366x768  | 15.3 | 2011 | [0963F0535BA1](<Digital/AU Optronics/AUO21EC/0963F0535BA1>) |
| AU Optronics     | AUO21EC | B156XW02 V1      | 1366x768  | 15.3 | 2008 | [2B6D2A9ECC99](<Digital/AU Optronics/AUO21EC/2B6D2A9ECC99>) |
| AU Optronics     | AUO21EC | B156XTK02        | 1366x768  | 15.3 |      | [16372BB51CD1](<Digital/AU Optronics/AUO21EC/16372BB51CD1>) |
| AU Optronics     | AUO21ED |                  | 1920x1080 | 15.3 | 2022 | [5BE73C4B84D8](<Digital/AU Optronics/AUO21ED/5BE73C4B84D8>) |
| AU Optronics     | AUO21ED | B156HAN02.1      | 1920x1080 | 15.3 | 2021 | [54FFECB9CE43](<Digital/AU Optronics/AUO21ED/54FFECB9CE43>) |
| AU Optronics     | AUO21ED |                  | 1920x1080 | 15.3 | 2019 | [7322E5E5CE7B](<Digital/AU Optronics/AUO21ED/7322E5E5CE7B>) |
| AU Optronics     | AUO21ED |                  | 1920x1080 | 15.3 | 2018 | [2F629386072F](<Digital/AU Optronics/AUO21ED/2F629386072F>) |
| AU Optronics     | AUO21ED |                  | 1920x1080 | 15.3 | 2017 | [9FF3E3099994](<Digital/AU Optronics/AUO21ED/9FF3E3099994>) |
| AU Optronics     | AUO21ED | B156HAN02.1      | 1920x1080 | 15.3 | 2016 | [0DB4F440FC11](<Digital/AU Optronics/AUO21ED/0DB4F440FC11>) |
| AU Optronics     | AUO21ED | C0T2R            | 1920x1080 | 15.3 | 2012 | [7736D8A16B11](<Digital/AU Optronics/AUO21ED/7736D8A16B11>) |
| AU Optronics     | AUO21ED | B156HW02 V1      | 1920x1080 | 15.3 | 2011 | [27261C5110CB](<Digital/AU Optronics/AUO21ED/27261C5110CB>) |
| AU Optronics     | AUO222B |                  | 3840x2160 | 13.2 | 2017 | [099FD7689920](<Digital/AU Optronics/AUO222B/099FD7689920>) |
| AU Optronics     | AUO222C | B133XW02 V2      | 1366x768  | 13.0 | 2008 | [1E117824F791](<Digital/AU Optronics/AUO222C/1E117824F791>) |
| AU Optronics     | AUO222D | B133HAK02.2      | 1920x1080 | 13.2 | 2018 | [0F310AAF3D19](<Digital/AU Optronics/AUO222D/0F310AAF3D19>) |
| AU Optronics     | AUO2236 | B140QAN02.2      | 2560x1440 | 13.9 | 2017 | [A7FD074079AA](<Digital/AU Optronics/AUO2236/A7FD074079AA>) |
| AU Optronics     | AUO223C |                  | 1366x768  | 13.9 | 2010 | [453F641F0EC4](<Digital/AU Optronics/AUO223C/453F641F0EC4>) |
| AU Optronics     | AUO223D | B140HTN02.2      | 1920x1080 | 13.9 | 2019 | [F1F104305C36](<Digital/AU Optronics/AUO223D/F1F104305C36>) |
| AU Optronics     | AUO223D | RVFT5            | 1920x1080 | 13.9 | 2017 | [DA6A177C9BF6](<Digital/AU Optronics/AUO223D/DA6A177C9BF6>) |
| AU Optronics     | AUO223E | M4RTT            | 1600x900  | 13.9 | 2012 | [54494A725BE9](<Digital/AU Optronics/AUO223E/54494A725BE9>) |
| AU Optronics     | AUO223E |                  | 1600x900  | 13.9 | 2010 | [4E8BDF246193](<Digital/AU Optronics/AUO223E/4E8BDF246193>) |
| AU Optronics     | AUO225C | B116XTN02.2      | 1366x768  | 11.6 | 2014 | [514DEDCD4F80](<Digital/AU Optronics/AUO225C/514DEDCD4F80>) |
| AU Optronics     | AUO226D |                  | 1920x1080 | 12.7 | 2015 | [0D466AAD527C](<Digital/AU Optronics/AUO226D/0D466AAD527C>) |
| AU Optronics     | AUO2274 | W651G 1AMUt      | 1280x800  | 15.4 | 2008 | [03FF62AA1AB9](<Digital/AU Optronics/AUO2274/03FF62AA1AB9>) |
| AU Optronics     | AUO2274 | PY599 ,;GPn      | 1280x800  | 15.4 | 2006 | [14BD4CE07E6D](<Digital/AU Optronics/AUO2274/14BD4CE07E6D>) |
| AU Optronics     | AUO2274 | N876G            | 1280x800  | 15.4 |      | [F99C779559B8](<Digital/AU Optronics/AUO2274/F99C779559B8>) |
| AU Optronics     | AUO2277 | B154PW02 V2      | 1440x900  | 15.4 | 2006 | [CCAE129213D9](<Digital/AU Optronics/AUO2277/CCAE129213D9>) |
| AU Optronics     | AUO2290 | WDF3Y            | 1920x1200 | 14.0 | 2020 | [38B4DFE146D9](<Digital/AU Optronics/AUO2290/38B4DFE146D9>) |
| AU Optronics     | AUO229E |                  | 1920x1080 | 13.9 | 2021 | [4DB5246E4F31](<Digital/AU Optronics/AUO229E/4DB5246E4F31>) |
| AU Optronics     | AUO229E |                  | 1600x900  | 17.1 | 2018 | [1309348A57C3](<Digital/AU Optronics/AUO229E/1309348A57C3>) |
| AU Optronics     | AUO229E | B173RTN02.2      | 1600x900  | 17.1 | 2017 | [011ED2A1EB7F](<Digital/AU Optronics/AUO229E/011ED2A1EB7F>) |
| AU Optronics     | AUO229E | B173RTN02.2      | 1600x900  | 17.1 | 2015 | [0B9760DF5052](<Digital/AU Optronics/AUO229E/0B9760DF5052>) |
| AU Optronics     | AUO22A7 |                  | 1920x1080 | 13.9 | 2022 | [3C35246FC4FC](<Digital/AU Optronics/AUO22A7/3C35246FC4FC>) |
| AU Optronics     | AUO22EB |                  | 3840x2160 | 15.7 | 2017 | [FBDFA3E6E690](<Digital/AU Optronics/AUO22EB/FBDFA3E6E690>) |
| AU Optronics     | AUO22EC | B156XTN02.2      | 1366x768  | 15.3 | 2016 | [6852C959AB55](<Digital/AU Optronics/AUO22EC/6852C959AB55>) |
| AU Optronics     | AUO22EC | B156XTN02.2      | 1366x768  | 15.3 | 2011 | [23C9CB2DC0DB](<Digital/AU Optronics/AUO22EC/23C9CB2DC0DB>) |
| AU Optronics     | AUO22EC | B156XW02 V2      | 1366x768  | 15.3 | 2009 | [717E5F5EA51D](<Digital/AU Optronics/AUO22EC/717E5F5EA51D>) |
| AU Optronics     | AUO22ED | T1NG3            | 1920x1080 | 15.3 | 2018 | [46CFB90CD989](<Digital/AU Optronics/AUO22ED/46CFB90CD989>) |
| AU Optronics     | AUO22ED |                  | 1920x1080 | 15.3 | 2016 | [BEFAE05B6156](<Digital/AU Optronics/AUO22ED/BEFAE05B6156>) |
| AU Optronics     | AUO22ED |                  | 1920x1080 | 15.3 |      | [A0ADE5C43C78](<Digital/AU Optronics/AUO22ED/A0ADE5C43C78>) |
| AU Optronics     | AUO232B | B133ZAN02.3      | 3840x2160 | 13.2 | 2017 | [078F765D3CE6](<Digital/AU Optronics/AUO232B/078F765D3CE6>) |
| AU Optronics     | AUO232D |                  | 1920x1080 | 13.2 | 2018 | [6DB3946697A6](<Digital/AU Optronics/AUO232D/6DB3946697A6>) |
| AU Optronics     | AUO232D |                  | 1920x1080 | 13.2 | 2013 | [24CA15117A2C](<Digital/AU Optronics/AUO232D/24CA15117A2C>) |
| AU Optronics     | AUO2336 | B140QAN02.3      | 2560x1440 | 13.9 | 2017 | [E47BA8047D4A](<Digital/AU Optronics/AUO2336/E47BA8047D4A>) |
| AU Optronics     | AUO233C | 9TMDG            | 1366x768  | 13.9 | 2012 | [051CF32AFBBC](<Digital/AU Optronics/AUO233C/051CF32AFBBC>) |
| AU Optronics     | AUO233C | B140XW02 V3      | 1366x768  | 13.9 | 2009 | [BA3DFB033E24](<Digital/AU Optronics/AUO233C/BA3DFB033E24>) |
| AU Optronics     | AUO233C | B140XTN02        | 1366x768  | 13.9 |      | [4C0FDCAC5D32](<Digital/AU Optronics/AUO233C/4C0FDCAC5D32>) |
| AU Optronics     | AUO233D | B140HAK02.3      | 1920x1080 | 13.9 | 2017 | [441D51E547D2](<Digital/AU Optronics/AUO233D/441D51E547D2>) |
| AU Optronics     | AUO233E |                  | 1600x900  | 13.9 | 2012 | [3B4C88189955](<Digital/AU Optronics/AUO233E/3B4C88189955>) |
| AU Optronics     | AUO2344 | B141EW02 V3      | 1280x800  | 14.0 |      | [6620DEAFE7C6](<Digital/AU Optronics/AUO2344/6620DEAFE7C6>) |
| AU Optronics     | AUO2351 | JF383            | 1024x768  | 14.9 |      | [3D2741F16D24](<Digital/AU Optronics/AUO2351/3D2741F16D24>) |
| AU Optronics     | AUO235C | J0N5T            | 1366x768  | 11.6 | 2020 | [C1BA72317D27](<Digital/AU Optronics/AUO235C/C1BA72317D27>) |
| AU Optronics     | AUO235C |                  | 1366x768  | 11.6 | 2018 | [8A30EAF65C5E](<Digital/AU Optronics/AUO235C/8A30EAF65C5E>) |
| AU Optronics     | AUO235C | V4VFK            | 1366x768  | 11.6 | 2017 | [06BA16772CD9](<Digital/AU Optronics/AUO235C/06BA16772CD9>) |
| AU Optronics     | AUO235C | 7KKCG            | 1366x768  | 11.6 | 2015 | [64EFC7D32BCB](<Digital/AU Optronics/AUO235C/64EFC7D32BCB>) |
| AU Optronics     | AUO235C |                  | 1366x768  | 11.6 | 2014 | [3244099C923B](<Digital/AU Optronics/AUO235C/3244099C923B>) |
| AU Optronics     | AUO235C | B116XTN02.3      | 1366x768  | 11.6 | 2013 | [B40F22B3F308](<Digital/AU Optronics/AUO235C/B40F22B3F308>) |
| AU Optronics     | AUO235C | FGF20            | 1366x768  | 11.6 |      | [AA2CB9095A5E](<Digital/AU Optronics/AUO235C/AA2CB9095A5E>) |
| AU Optronics     | AUO236D | M1GMV            | 1920x1080 | 12.7 | 2016 | [E0F196FE6286](<Digital/AU Optronics/AUO236D/E0F196FE6286>) |
| AU Optronics     | AUO2374 | N876G            | 1280x800  | 15.4 | 2008 | [9177B7A8E3EF](<Digital/AU Optronics/AUO2374/9177B7A8E3EF>) |
| AU Optronics     | AUO2374 | GR452 '6BJh      | 1280x800  | 15.4 | 2006 | [CF1E52890A69](<Digital/AU Optronics/AUO2374/CF1E52890A69>) |
| AU Optronics     | AUO2377 | T749J            | 1440x900  | 15.4 | 2009 | [CE222F8A90D7](<Digital/AU Optronics/AUO2377/CE222F8A90D7>) |
| AU Optronics     | AUO2380 | ''               | 1920x1080 | 24.1 | 2022 | [73D9EFF7322C](<Digital/AU Optronics/AUO2380/73D9EFF7322C>) |
| AU Optronics     | AUO238D | B156HTN06.2      | 1920x1080 | 15.3 | 2019 | [7C63285B11A0](<Digital/AU Optronics/AUO238D/7C63285B11A0>) |
| AU Optronics     | AUO239B |                  | 1366x768  | 11.6 | 2021 | [7C5769CE1A85](<Digital/AU Optronics/AUO239B/7C5769CE1A85>) |
| AU Optronics     | AUO23D2 | B101AW02 V3      | 1024x600  | 10.1 | 2009 | [7E5A5EE8F64E](<Digital/AU Optronics/AUO23D2/7E5A5EE8F64E>) |
| AU Optronics     | AUO23EC | B156XTN02.3      | 1366x768  | 15.3 | 2011 | [3FE0ABE4D1F7](<Digital/AU Optronics/AUO23EC/3FE0ABE4D1F7>) |
| AU Optronics     | AUO23EC | 3XJDG            | 1366x768  | 15.3 | 2010 | [AEFE534C2FA7](<Digital/AU Optronics/AUO23EC/AEFE534C2FA7>) |
| AU Optronics     | AUO23EC | W465R            | 1366x768  | 15.3 | 2009 | [02CE7E7112A6](<Digital/AU Optronics/AUO23EC/02CE7E7112A6>) |
| AU Optronics     | AUO23ED |                  | 1920x1080 | 15.3 | 2018 | [BC20230A1555](<Digital/AU Optronics/AUO23ED/BC20230A1555>) |
| AU Optronics     | AUO23ED | K1MP9            | 1920x1080 | 15.3 | 2017 | [3AC10C69EFE1](<Digital/AU Optronics/AUO23ED/3AC10C69EFE1>) |
| AU Optronics     | AUO23ED |                  | 1920x1080 | 15.3 | 2016 | [0139F7E6D8C9](<Digital/AU Optronics/AUO23ED/0139F7E6D8C9>) |
| AU Optronics     | AUO243C | B140XTN02.4      | 1366x768  | 13.9 | 2012 | [212639A9D707](<Digital/AU Optronics/AUO243C/212639A9D707>) |
| AU Optronics     | AUO243C | H3D38            | 1366x768  | 13.9 | 2009 | [C56708B1D5B4](<Digital/AU Optronics/AUO243C/C56708B1D5B4>) |
| AU Optronics     | AUO243D | RWGX1            | 1920x1080 | 13.9 | 2021 | [8F74C930B4B3](<Digital/AU Optronics/AUO243D/8F74C930B4B3>) |
| AU Optronics     | AUO243D | B140HAN02.4      | 1920x1080 | 13.9 | 2018 | [513F0DC01C3D](<Digital/AU Optronics/AUO243D/513F0DC01C3D>) |
| AU Optronics     | AUO243D | B140HAN02.4      | 1920x1080 | 13.9 | 2017 | [75B0FE542DC6](<Digital/AU Optronics/AUO243D/75B0FE542DC6>) |
| AU Optronics     | AUO243D | B140HAN02.4      | 1920x1080 | 13.9 | 2016 | [DD7A8A403705](<Digital/AU Optronics/AUO243D/DD7A8A403705>) |
| AU Optronics     | AUO243D | 9PN3R            | 1920x1080 | 13.9 |      | [352EDE67A027](<Digital/AU Optronics/AUO243D/352EDE67A027>) |
| AU Optronics     | AUO2451 | B150XG02 V4      | 1024x768  | 14.9 |      | [FB23F4AECB22](<Digital/AU Optronics/AUO2451/FB23F4AECB22>) |
| AU Optronics     | AUO248C | B140HAN06.8      | 1920x1080 | 13.9 | 2019 | [8BBC162FFBB7](<Digital/AU Optronics/AUO248C/8BBC162FFBB7>) |
| AU Optronics     | AUO24EC | B156XTN02.4      | 1366x768  | 15.3 | 2011 | [ADEC1CD8F67F](<Digital/AU Optronics/AUO24EC/ADEC1CD8F67F>) |
| AU Optronics     | AUO24ED | F8FGD            | 1920x1080 | 15.3 | 2019 | [C14B7ECEA1C5](<Digital/AU Optronics/AUO24ED/C14B7ECEA1C5>) |
| AU Optronics     | AUO24ED | 6CG7W            | 1920x1080 | 15.3 | 2018 | [001517756BEF](<Digital/AU Optronics/AUO24ED/001517756BEF>) |
| AU Optronics     | AUO24ED |                  | 1920x1080 | 15.3 | 2016 | [853F0540E874](<Digital/AU Optronics/AUO24ED/853F0540E874>) |
| AU Optronics     | AUO252B | 6VR5V            | 3840x2160 | 13.2 | 2018 | [732333F0FF60](<Digital/AU Optronics/AUO252B/732333F0FF60>) |
| AU Optronics     | AUO253C |                  | 1366x768  | 13.9 | 2012 | [38617F4613A6](<Digital/AU Optronics/AUO253C/38617F4613A6>) |
| AU Optronics     | AUO253D | B140HAK02.5      | 1920x1080 | 13.9 | 2018 | [17512C3408FA](<Digital/AU Optronics/AUO253D/17512C3408FA>) |
| AU Optronics     | AUO253D | B140HAN02.5      | 1920x1080 | 13.9 | 2016 | [85F14B9F0E14](<Digital/AU Optronics/AUO253D/85F14B9F0E14>) |
| AU Optronics     | AUO255C | B116XTN02.5      | 1366x768  | 11.6 | 2014 | [3D08AE334A19](<Digital/AU Optronics/AUO255C/3D08AE334A19>) |
| AU Optronics     | AUO2574 | B154EW02 V5      | 1280x800  | 15.4 | 2006 | [71C83E45A95F](<Digital/AU Optronics/AUO2574/71C83E45A95F>) |
| AU Optronics     | AUO258C | B140HAN06.9      | 1920x1080 | 13.9 | 2019 | [589DE605E274](<Digital/AU Optronics/AUO258C/589DE605E274>) |
| AU Optronics     | AUO259B | 2M5HF            | 1920x1200 | 14.0 | 2021 | [59588C5B4FDF](<Digital/AU Optronics/AUO259B/59588C5B4FDF>) |
| AU Optronics     | AUO25EC | T5CDR            | 1366x768  | 15.3 | 2009 | [140F9746B73B](<Digital/AU Optronics/AUO25EC/140F9746B73B>) |
| AU Optronics     | AUO25ED | B156HAN02.5      | 1920x1080 | 15.3 | 2019 | [C3F090289482](<Digital/AU Optronics/AUO25ED/C3F090289482>) |
| AU Optronics     | AUO25ED | 1K1DG            | 1920x1080 | 15.3 | 2018 | [7960B69A1331](<Digital/AU Optronics/AUO25ED/7960B69A1331>) |
| AU Optronics     | AUO25ED | B156HW02 V5      | 1920x1080 | 15.3 | 2010 | [404456372465](<Digital/AU Optronics/AUO25ED/404456372465>) |
| AU Optronics     | AUO263D | KJY05            | 1920x1080 | 13.9 | 2018 | [ACA0F475502E](<Digital/AU Optronics/AUO263D/ACA0F475502E>) |
| AU Optronics     | AUO263D | V8HK9            | 1920x1080 | 13.9 | 2017 | [B5F154A0FB02](<Digital/AU Optronics/AUO263D/B5F154A0FB02>) |
| AU Optronics     | AUO2674 | B154EW02 V6      | 1280x800  | 15.4 | 2006 | [DD81D1F57A4B](<Digital/AU Optronics/AUO2674/DD81D1F57A4B>) |
| AU Optronics     | AUO2698 | B140QAN05.H      | 2240x1400 | 14.0 | 2020 | [F39354B58CD6](<Digital/AU Optronics/AUO2698/F39354B58CD6>) |
| AU Optronics     | AUO26A4 |                  | 2880x1800 | 14.0 | 2022 | [106041F476A9](<Digital/AU Optronics/AUO26A4/106041F476A9>) |
| AU Optronics     | AUO26A9 | B160QAN02.3      | 2560x1600 | 15.9 | 2022 | [0CE5380C48FC](<Digital/AU Optronics/AUO26A9/0CE5380C48FC>) |
| AU Optronics     | AUO26EC | B156XTN02.6      | 1366x768  | 15.3 | 2012 | [CA2BB0B656E6](<Digital/AU Optronics/AUO26EC/CA2BB0B656E6>) |
| AU Optronics     | AUO26EC | B156XW02 V6      | 1366x768  | 15.3 | 2009 | [BF767DF2D021](<Digital/AU Optronics/AUO26EC/BF767DF2D021>) |
| AU Optronics     | AUO26ED | GHW1K            | 1920x1080 | 15.3 | 2018 | [61D44DE0B28D](<Digital/AU Optronics/AUO26ED/61D44DE0B28D>) |
| AU Optronics     | AUO272B |                  | 3840x2160 | 13.2 | 2018 | [28456E1A90BC](<Digital/AU Optronics/AUO272B/28456E1A90BC>) |
| AU Optronics     | AUO272D | B133HAN02.7      | 1920x1080 | 13.2 | 2015 | [A402FE627F55](<Digital/AU Optronics/AUO272D/A402FE627F55>) |
| AU Optronics     | AUO275C | B116XAN02.7      | 1366x768  | 11.6 | 2014 | [9790A3D1A65D](<Digital/AU Optronics/AUO275C/9790A3D1A65D>) |
| AU Optronics     | AUO2774 | Y286G            | 1280x800  | 15.4 | 2008 | [EA5C100A6261](<Digital/AU Optronics/AUO2774/EA5C100A6261>) |
| AU Optronics     | AUO2774 | B154EW02 V7      | 1280x800  | 15.4 | 2007 | [5C2A81CF1577](<Digital/AU Optronics/AUO2774/5C2A81CF1577>) |
| AU Optronics     | AUO2774 | B154EW02 V7      | 1280x800  | 15.4 | 2006 | [A6A268BC8CA7](<Digital/AU Optronics/AUO2774/A6A268BC8CA7>) |
| AU Optronics     | AUO278E | B173ZAN05.0      | 3840x2160 | 17.1 | 2019 | [B50DB03D0BD4](<Digital/AU Optronics/AUO278E/B50DB03D0BD4>) |
| AU Optronics     | AUO2792 |                  | 1920x1080 | 17.3 | 2020 | [451BCB7FFC65](<Digital/AU Optronics/AUO2792/451BCB7FFC65>) |
| AU Optronics     | AUO27B5 | B160QAN04.T      | 3200x2000 | 15.9 | 2024 | [92C304C56797](<Digital/AU Optronics/AUO27B5/92C304C56797>) |
| AU Optronics     | AUO27EC | B156XW02 V7      | 1366x768  | 15.3 | 2011 | [1B1CE65D0FBE](<Digital/AU Optronics/AUO27EC/1B1CE65D0FBE>) |
| AU Optronics     | AUO27ED |                  | 1920x1080 | 15.3 | 2018 | [C1BD5902D4E6](<Digital/AU Optronics/AUO27ED/C1BD5902D4E6>) |
| AU Optronics     | AUO282B | 90NTH            | 3840x2160 | 13.2 | 2018 | [5F748044B99F](<Digital/AU Optronics/AUO282B/5F748044B99F>) |
| AU Optronics     | AUO283C |                  | 1366x768  | 13.9 | 2013 | [D8FBD9AAE475](<Digital/AU Optronics/AUO283C/D8FBD9AAE475>) |
| AU Optronics     | AUO288C |                  | 1366x768  | 11.6 | 2019 | [AB3EFD6E34D4](<Digital/AU Optronics/AUO288C/AB3EFD6E34D4>) |
| AU Optronics     | AUO2892 | PV7KJ            | 3840x2160 | 17.1 | 2021 | [AF169B74B9E2](<Digital/AU Optronics/AUO2892/AF169B74B9E2>) |
| AU Optronics     | AUO28B2 | B160QAN02.N      | 2560x1600 | 15.9 | 2024 | [598484914457](<Digital/AU Optronics/AUO28B2/598484914457>) |
| AU Optronics     | AUO28ED | B156HAN02.8      | 1920x1080 | 15.3 | 2016 | [0EDB28EF02E7](<Digital/AU Optronics/AUO28ED/0EDB28EF02E7>) |
| AU Optronics     | AUO293C | B140XTN02.9      | 1366x768  | 13.9 | 2013 | [30DAA7F47C89](<Digital/AU Optronics/AUO293C/30DAA7F47C89>) |
| AU Optronics     | AUO2992 |                  | 1920x1080 | 15.3 | 2020 | [870A4122DB94](<Digital/AU Optronics/AUO2992/870A4122DB94>) |
| AU Optronics     | AUO299C | D42V5            | 1920x1080 | 17.3 | 2021 | [AB6E8D23C8B8](<Digital/AU Optronics/AUO299C/AB6E8D23C8B8>) |
| AU Optronics     | AUO2A2B |                  | 3840x2160 | 13.2 | 2019 | [C93F0D55F9F1](<Digital/AU Optronics/AUO2A2B/C93F0D55F9F1>) |
| AU Optronics     | AUO2A3C | 4Y5YH            | 1366x768  | 13.9 | 2013 | [06FA8E187144](<Digital/AU Optronics/AUO2A3C/06FA8E187144>) |
| AU Optronics     | AUO2B2B | KCN6G            | 3840x2160 | 13.2 |      | [7B678F0B5915](<Digital/AU Optronics/AUO2B2B/7B678F0B5915>) |
| AU Optronics     | AUO2B3C | B140XTN02.B      | 1366x768  | 13.9 | 2018 | [9F2B39443B50](<Digital/AU Optronics/AUO2B3C/9F2B39443B50>) |
| AU Optronics     | AUO2B99 | 5GTK0            | 1920x1080 | 13.2 | 2021 | [F00F849E0551](<Digital/AU Optronics/AUO2B99/F00F849E0551>) |
| AU Optronics     | AUO2B9B | GRGX1            | 2240x1400 | 14.0 | 2021 | [FB63A9CCD7D0](<Digital/AU Optronics/AUO2B9B/FB63A9CCD7D0>) |
| AU Optronics     | AUO2BAB |                  | 1920x1200 | 14.0 | 2023 | [7E28D77B514D](<Digital/AU Optronics/AUO2BAB/7E28D77B514D>) |
| AU Optronics     | AUO2BB4 | B160UAN06.N      | 1920x1200 | 15.9 | 2024 | [48B6C4D63934](<Digital/AU Optronics/AUO2BB4/48B6C4D63934>) |
| AU Optronics     | AUO2C3C | B140XTN02.C      | 1366x768  | 13.9 | 2012 | [AB3BADB9732F](<Digital/AU Optronics/AUO2C3C/AB3BADB9732F>) |
| AU Optronics     | AUO2C9F |                  | 1920x1200 | 13.4 | 2021 | [6B3C698578FA](<Digital/AU Optronics/AUO2C9F/6B3C698578FA>) |
| AU Optronics     | AUO2D3C | KRMXW            | 1366x768  | 13.9 | 2015 | [1422E78BF94A](<Digital/AU Optronics/AUO2D3C/1422E78BF94A>) |
| AU Optronics     | AUO2D3C | B140XTN02.D      | 1366x768  | 13.9 | 2013 | [45064B6E9A8D](<Digital/AU Optronics/AUO2D3C/45064B6E9A8D>) |
| AU Optronics     | AUO2DB8 | PKD5W            | 2560x1600 | 14.0 | 2024 | [EE6BDA60452B](<Digital/AU Optronics/AUO2DB8/EE6BDA60452B>) |
| AU Optronics     | AUO2E3C |                  | 1366x768  | 13.9 | 2017 | [6292A862282F](<Digital/AU Optronics/AUO2E3C/6292A862282F>) |
| AU Optronics     | AUO2E3C | H4NVF            | 1366x768  | 13.9 | 2016 | [ACBD4309E598](<Digital/AU Optronics/AUO2E3C/ACBD4309E598>) |
| AU Optronics     | AUO2E3C | KFC4D            | 1366x768  | 13.9 | 2015 | [666BB00642D8](<Digital/AU Optronics/AUO2E3C/666BB00642D8>) |
| AU Optronics     | AUO2E3C |                  | 1366x768  | 13.9 | 2013 | [1EE0787A6FAB](<Digital/AU Optronics/AUO2E3C/1EE0787A6FAB>) |
| AU Optronics     | AUO2E8D | B156HAN02.1      | 1920x1080 | 15.3 | 2019 | [9F308339E24E](<Digital/AU Optronics/AUO2E8D/9F308339E24E>) |
| AU Optronics     | AUO2EA5 |                  | 3840x2400 | 15.9 | 2022 | [BA54C804F066](<Digital/AU Optronics/AUO2EA5/BA54C804F066>) |
| AU Optronics     | AUO2FA6 |                  | 1920x1080 | 13.9 | 2022 | [161704E39646](<Digital/AU Optronics/AUO2FA6/161704E39646>) |
| AU Optronics     | AUO3014 | DF892 +:FOn      | 1280x800  | 12.0 | 2006 | [F0F1F0FC6F1E](<Digital/AU Optronics/AUO3014/F0F1F0FC6F1E>) |
| AU Optronics     | AUO302C |                  | 1366x768  | 13.2 | 2019 | [37E67C53E1C5](<Digital/AU Optronics/AUO302C/37E67C53E1C5>) |
| AU Optronics     | AUO302C |                  | 1366x768  | 13.2 | 2018 | [3D7C0966647B](<Digital/AU Optronics/AUO302C/3D7C0966647B>) |
| AU Optronics     | AUO302C | B133XW03 V0      | 1366x768  | 13.0 | 2011 | [6276FCC584E9](<Digital/AU Optronics/AUO302C/6276FCC584E9>) |
| AU Optronics     | AUO302C | 301F4            | 1366x768  | 13.0 | 2010 | [5082538ACCA0](<Digital/AU Optronics/AUO302C/5082538ACCA0>) |
| AU Optronics     | AUO302D | B133HAT03.0      | 1920x1080 | 13.2 | 2018 | [AE7D31D29E14](<Digital/AU Optronics/AUO302D/AE7D31D29E14>) |
| AU Optronics     | AUO302D | B133HAN03.0      | 1920x1080 | 13.6 | 2012 | [9B3810B15918](<Digital/AU Optronics/AUO302D/9B3810B15918>) |
| AU Optronics     | AUO303C | C1JKP            | 1366x768  | 13.9 | 2011 | [6B6379A9F025](<Digital/AU Optronics/AUO303C/6B6379A9F025>) |
| AU Optronics     | AUO303C | B140XTN03.0      | 1366x768  | 13.9 | 2010 | [00585BF9CAB7](<Digital/AU Optronics/AUO303C/00585BF9CAB7>) |
| AU Optronics     | AUO303C | B140XW03 V0      | 1366x768  | 13.9 | 2009 | [A387368ACDFB](<Digital/AU Optronics/AUO303C/A387368ACDFB>) |
| AU Optronics     | AUO303D | B140HAK03.0      | 1920x1080 | 13.9 | 2019 | [29599991371A](<Digital/AU Optronics/AUO303D/29599991371A>) |
| AU Optronics     | AUO303D | B140HAK03.0      | 1920x1080 | 13.9 | 2018 | [5C911BAE74DB](<Digital/AU Optronics/AUO303D/5C911BAE74DB>) |
| AU Optronics     | AUO303D | B140HAN03.0      | 1920x1080 | 13.9 | 2016 | [662F5E92EAFC](<Digital/AU Optronics/AUO303D/662F5E92EAFC>) |
| AU Optronics     | AUO303E | 6TH09            | 1600x900  | 13.9 | 2015 | [A0F513CFB2FE](<Digital/AU Optronics/AUO303E/A0F513CFB2FE>) |
| AU Optronics     | AUO303E | B140RTN03.0      | 1600x900  | 13.9 | 2012 | [101792CFE9FD](<Digital/AU Optronics/AUO303E/101792CFE9FD>) |
| AU Optronics     | AUO303E |                  | 1600x900  | 13.9 | 2011 | [85582E35163A](<Digital/AU Optronics/AUO303E/85582E35163A>) |
| AU Optronics     | AUO3047 | GR584 #2=Fd      | 1440x900  | 14.0 | 2007 | [3D27D922536F](<Digital/AU Optronics/AUO3047/3D27D922536F>) |
| AU Optronics     | AUO305C |                  | 1366x768  | 11.6 | 2012 | [161EA0D41E7D](<Digital/AU Optronics/AUO305C/161EA0D41E7D>) |
| AU Optronics     | AUO305C | 2VD2K            | 1366x768  | 11.6 | 2011 | [76FA508D9595](<Digital/AU Optronics/AUO305C/76FA508D9595>) |
| AU Optronics     | AUO305C | B116XW03 V0      | 1366x768  | 11.6 | 2009 | [75F85E03DB30](<Digital/AU Optronics/AUO305C/75F85E03DB30>) |
| AU Optronics     | AUO305D | B116HAN03.0      | 1920x1080 | 11.6 | 2012 | [E8203CCBEDDF](<Digital/AU Optronics/AUO305D/E8203CCBEDDF>) |
| AU Optronics     | AUO306D | B125HAN03.0      | 1920x1080 | 12.7 | 2016 | [89EED14E54AB](<Digital/AU Optronics/AUO306D/89EED14E54AB>) |
| AU Optronics     | AUO309B | B173ZAN03.0      | 3840x2160 | 17.1 | 2019 | [6EFE162AF976](<Digital/AU Optronics/AUO309B/6EFE162AF976>) |
| AU Optronics     | AUO309B | B173ZAN03        | 3840x2160 | 17.1 |      | [50C7673ADAE6](<Digital/AU Optronics/AUO309B/50C7673ADAE6>) |
| AU Optronics     | AUO309D |                  | 1920x1080 | 17.1 | 2017 | [F22871DBB016](<Digital/AU Optronics/AUO309D/F22871DBB016>) |
| AU Optronics     | AUO30A5 | P3FPJ            | 2560x1600 | 15.9 | 2022 | [A96952E8921D](<Digital/AU Optronics/AUO30A5/A96952E8921D>) |
| AU Optronics     | AUO30D2 | C050T            | 1024x600  | 10.1 | 2009 | [1F11C4AC4461](<Digital/AU Optronics/AUO30D2/1F11C4AC4461>) |
| AU Optronics     | AUO30D2 | B101AW03 V0      | 1024x600  | 10.1 | 2008 | [4D64C3878185](<Digital/AU Optronics/AUO30D2/4D64C3878185>) |
| AU Optronics     | AUO30EB |                  | 3840x2160 | 15.3 | 2018 | [58ADD41120A7](<Digital/AU Optronics/AUO30EB/58ADD41120A7>) |
| AU Optronics     | AUO30EB |                  | 3840x2160 | 15.3 | 2017 | [231839101FC4](<Digital/AU Optronics/AUO30EB/231839101FC4>) |
| AU Optronics     | AUO30EC | B156XW03 V0      | 1366x768  | 15.3 | 2009 | [DF645449A8D4](<Digital/AU Optronics/AUO30EC/DF645449A8D4>) |
| AU Optronics     | AUO30ED | B156HAK03.0      | 1920x1080 | 15.3 | 2017 | [5000B2E9EF7A](<Digital/AU Optronics/AUO30ED/5000B2E9EF7A>) |
| AU Optronics     | AUO30ED | XWN1R            | 1920x1080 | 15.3 | 2016 | [9BBA1F5348B5](<Digital/AU Optronics/AUO30ED/9BBA1F5348B5>) |
| AU Optronics     | AUO30ED | B156HAN03.0      | 1920x1080 | 15.3 | 2013 | [0DCB9F3ECAE9](<Digital/AU Optronics/AUO30ED/0DCB9F3ECAE9>) |
| AU Optronics     | AUO30ED | B156HTN03.0      | 1920x1080 | 15.3 | 2012 | [4EC3F6F3CBCD](<Digital/AU Optronics/AUO30ED/4EC3F6F3CBCD>) |
| AU Optronics     | AUO30ED | 00R4M            | 1920x1080 | 15.3 | 2010 | [C2C2BE694B3C](<Digital/AU Optronics/AUO30ED/C2C2BE694B3C>) |
| AU Optronics     | AUO3114 |                  | 1280x800  | 12.0 | 2006 | [75FA1316959A](<Digital/AU Optronics/AUO3114/75FA1316959A>) |
| AU Optronics     | AUO312C | G50X6            | 1366x768  | 13.2 | 2018 | [ADBC13D13B88](<Digital/AU Optronics/AUO312C/ADBC13D13B88>) |
| AU Optronics     | AUO312C | 9D0GV            | 1366x768  | 13.0 | 2012 | [B739ADB112B1](<Digital/AU Optronics/AUO312C/B739ADB112B1>) |
| AU Optronics     | AUO312C |                  | 1366x768  | 13.0 | 2011 | [4BC65E9274D0](<Digital/AU Optronics/AUO312C/4BC65E9274D0>) |
| AU Optronics     | AUO312C | B133XW03 V1      | 1366x768  | 13.0 | 2010 | [105469124880](<Digital/AU Optronics/AUO312C/105469124880>) |
| AU Optronics     | AUO313C | B140XTN03.1      | 1366x768  | 13.9 | 2012 | [A6534F58F461](<Digital/AU Optronics/AUO313C/A6534F58F461>) |
| AU Optronics     | AUO313C | HPK92            | 1366x768  | 13.9 | 2011 | [14660F913DC2](<Digital/AU Optronics/AUO313C/14660F913DC2>) |
| AU Optronics     | AUO313C | B140XW03 V1      | 1366x768  | 13.9 | 2010 | [61101F2E9E24](<Digital/AU Optronics/AUO313C/61101F2E9E24>) |
| AU Optronics     | AUO313D | 33GTF            | 1920x1080 | 13.9 | 2020 | [ECE6AA72002E](<Digital/AU Optronics/AUO313D/ECE6AA72002E>) |
| AU Optronics     | AUO313D | C8TCK            | 1920x1080 | 13.9 | 2019 | [E1954343D298](<Digital/AU Optronics/AUO313D/E1954343D298>) |
| AU Optronics     | AUO313D | PD7J9            | 1920x1080 | 13.9 | 2018 | [AF8F79F5FEF9](<Digital/AU Optronics/AUO313D/AF8F79F5FEF9>) |
| AU Optronics     | AUO313D | B140HAN03.1      | 1920x1080 | 13.9 | 2016 | [A892464EA311](<Digital/AU Optronics/AUO313D/A892464EA311>) |
| AU Optronics     | AUO313E |                  | 1600x900  | 13.9 | 2012 | [6DEFBC6B77F6](<Digital/AU Optronics/AUO313E/6DEFBC6B77F6>) |
| AU Optronics     | AUO313E | T6N3N            | 1600x900  | 13.9 | 2010 | [655F2364AD0F](<Digital/AU Optronics/AUO313E/655F2364AD0F>) |
| AU Optronics     | AUO315C | B116XAT03.1      | 1366x768  | 11.6 | 2013 | [EA347BB4AB35](<Digital/AU Optronics/AUO315C/EA347BB4AB35>) |
| AU Optronics     | AUO315C | B116XW03 V1      | 1366x768  | 11.6 | 2012 | [328E27144BAE](<Digital/AU Optronics/AUO315C/328E27144BAE>) |
| AU Optronics     | AUO315C |                  | 1366x768  | 11.6 | 2011 | [DD551993E5F2](<Digital/AU Optronics/AUO315C/DD551993E5F2>) |
| AU Optronics     | AUO315C | B116XW03 V1      | 1366x768  | 11.6 | 2010 | [540635851CD9](<Digital/AU Optronics/AUO315C/540635851CD9>) |
| AU Optronics     | AUO315D | B116HAN03.1      | 1920x1080 | 11.6 | 2012 | [E6992008A1AD](<Digital/AU Optronics/AUO315D/E6992008A1AD>) |
| AU Optronics     | AUO316D |                  | 1920x1080 | 12.7 | 2016 | [88D25CAD0B3A](<Digital/AU Optronics/AUO316D/88D25CAD0B3A>) |
| AU Optronics     | AUO3187 | B170PW03 V1      | 1440x900  | 17.2 |      | [8840F435E2AB](<Digital/AU Optronics/AUO3187/8840F435E2AB>) |
| AU Optronics     | AUO3191 |                  | 1366x768  | 15.3 | 2020 | [1C1515C7AEE7](<Digital/AU Optronics/AUO3191/1C1515C7AEE7>) |
| AU Optronics     | AUO319D | B173HAN03.1      | 1920x1080 | 17.1 | 2017 | [5FFB984728CA](<Digital/AU Optronics/AUO319D/5FFB984728CA>) |
| AU Optronics     | AUO31A6 | 8G0JV            | 1920x1200 | 15.9 | 2022 | [A73E6EAE9500](<Digital/AU Optronics/AUO31A6/A73E6EAE9500>) |
| AU Optronics     | AUO31D2 | PVPKF            | 1024x600  | 10.1 | 2009 | [28EE80A515FC](<Digital/AU Optronics/AUO31D2/28EE80A515FC>) |
| AU Optronics     | AUO31D2 | B101AW03 V1      | 1024x600  | 10.1 | 2008 | [8374C7259B52](<Digital/AU Optronics/AUO31D2/8374C7259B52>) |
| AU Optronics     | AUO31EB | B156ZAN03.1      | 3840x2160 | 15.3 | 2017 | [EF6D53ACABDA](<Digital/AU Optronics/AUO31EB/EF6D53ACABDA>) |
| AU Optronics     | AUO31EC | B156XTN03.1      | 1366x768  | 15.3 | 2012 | [1C43222DD119](<Digital/AU Optronics/AUO31EC/1C43222DD119>) |
| AU Optronics     | AUO31EC | B156XTN03.1      | 1366x768  | 15.3 | 2011 | [FB88ED296AA0](<Digital/AU Optronics/AUO31EC/FB88ED296AA0>) |
| AU Optronics     | AUO31EC | B156XW03 V1      | 1366x768  | 15.3 | 2009 | [0D84395078DF](<Digital/AU Optronics/AUO31EC/0D84395078DF>) |
| AU Optronics     | AUO31ED | B156HTN03.1      | 1920x1080 | 15.3 | 2012 | [5AF05C26E1D4](<Digital/AU Optronics/AUO31ED/5AF05C26E1D4>) |
| AU Optronics     | AUO3214 | JF298 +:FPp      | 1280x800  | 12.0 | 2006 | [C0B558F7036E](<Digital/AU Optronics/AUO3214/C0B558F7036E>) |
| AU Optronics     | AUO322C |                  | 1366x768  | 13.2 | 2018 | [9315CBEB9815](<Digital/AU Optronics/AUO322C/9315CBEB9815>) |
| AU Optronics     | AUO322C | B133XW03 V2      | 1366x768  | 13.0 | 2009 | [347DE84F0FA6](<Digital/AU Optronics/AUO322C/347DE84F0FA6>) |
| AU Optronics     | AUO323C | B140XTN03.2      | 1366x768  | 13.9 | 2013 | [1284654F1286](<Digital/AU Optronics/AUO323C/1284654F1286>) |
| AU Optronics     | AUO323C | B140XW03 V2      | 1366x768  | 13.9 | 2010 | [28B78495F58C](<Digital/AU Optronics/AUO323C/28B78495F58C>) |
| AU Optronics     | AUO323D | W2D6P            | 1920x1080 | 13.9 | 2020 | [8C1FE585DDA3](<Digital/AU Optronics/AUO323D/8C1FE585DDA3>) |
| AU Optronics     | AUO323D | B140HAK03.2      | 1920x1080 | 13.9 | 2018 | [29A0120B496A](<Digital/AU Optronics/AUO323D/29A0120B496A>) |
| AU Optronics     | AUO323D | B139HAN03.2      | 1920x1080 | 13.9 | 2015 | [A3255FA05728](<Digital/AU Optronics/AUO323D/A3255FA05728>) |
| AU Optronics     | AUO323D | B140HAN03        | 1920x1080 | 13.9 |      | [A12C4E8A4062](<Digital/AU Optronics/AUO323D/A12C4E8A4062>) |
| AU Optronics     | AUO323E | B140RTN03.2      | 1600x900  | 13.9 | 2012 | [03464833E92A](<Digital/AU Optronics/AUO323E/03464833E92A>) |
| AU Optronics     | AUO325C | B116XAN03.2      | 1366x768  | 11.6 | 2012 | [C0554B9AED3C](<Digital/AU Optronics/AUO325C/C0554B9AED3C>) |
| AU Optronics     | AUO325C | B116XW03 V2      | 1366x768  | 11.6 | 2011 | [672AE7503995](<Digital/AU Optronics/AUO325C/672AE7503995>) |
| AU Optronics     | AUO325C | B116XW03         | 1366x768  | 11.6 |      | [09BC588A4963](<Digital/AU Optronics/AUO325C/09BC588A4963>) |
| AU Optronics     | AUO325D | AUO^ B116HAT03.2 | 1920x1080 | 11.6 | 2012 | [03805B98D02C](<Digital/AU Optronics/AUO325D/03805B98D02C>) |
| AU Optronics     | AUO3287 | XD549 .AOX|      | 1440x900  | 17.2 |      | [F6E5B64A8966](<Digital/AU Optronics/AUO3287/F6E5B64A8966>) |
| AU Optronics     | AUO328E | B156HAN12.0      | 1920x1080 | 15.3 | 2019 | [20CEB0FB004B](<Digital/AU Optronics/AUO328E/20CEB0FB004B>) |
| AU Optronics     | AUO329B | 44TRN            | 3840x2160 | 17.1 | 2020 | [D635E110302E](<Digital/AU Optronics/AUO329B/D635E110302E>) |
| AU Optronics     | AUO329B | B173ZAN03.2      | 3840x2160 | 17.1 | 2019 | [560A1A1B0A58](<Digital/AU Optronics/AUO329B/560A1A1B0A58>) |
| AU Optronics     | AUO329D | B173HAN03.2      | 1920x1080 | 17.1 | 2018 | [8F8DB90D957E](<Digital/AU Optronics/AUO329D/8F8DB90D957E>) |
| AU Optronics     | AUO329D | B173HAN03.2      | 1920x1080 | 17.1 | 2017 | [1390B363E884](<Digital/AU Optronics/AUO329D/1390B363E884>) |
| AU Optronics     | AUO329F |                  | 2560x1600 | 13.4 | 2020 | [2ACB13ECC0E2](<Digital/AU Optronics/AUO329F/2ACB13ECC0E2>) |
| AU Optronics     | AUO32B0 | B156HANAA.0      | 1920x1080 | 15.3 | 2023 | [C5F505E451A5](<Digital/AU Optronics/AUO32B0/C5F505E451A5>) |
| AU Optronics     | AUO32EB | B156ZAN03.2      | 3840x2160 | 15.3 | 2017 | [04E9794EB8C2](<Digital/AU Optronics/AUO32EB/04E9794EB8C2>) |
| AU Optronics     | AUO32EC | JGP6V            | 1366x768  | 15.3 | 2012 | [089C9DF2EB60](<Digital/AU Optronics/AUO32EC/089C9DF2EB60>) |
| AU Optronics     | AUO32EC |                  | 1366x768  | 15.3 | 2011 | [816A42BD0BE7](<Digital/AU Optronics/AUO32EC/816A42BD0BE7>) |
| AU Optronics     | AUO32EC | B156XW03 V2      | 1366x768  | 15.3 | 2009 | [CAA06BCAD70E](<Digital/AU Optronics/AUO32EC/CAA06BCAD70E>) |
| AU Optronics     | AUO32ED |                  | 1920x1080 | 15.3 | 2012 | [E3BC0715FD0F](<Digital/AU Optronics/AUO32ED/E3BC0715FD0F>) |
| AU Optronics     | AUO3314 | B121EW03 V3      | 1280x800  | 12.0 | 2006 | [0DA33833A46F](<Digital/AU Optronics/AUO3314/0DA33833A46F>) |
| AU Optronics     | AUO332C | B133XTN03.3      | 1366x768  | 13.2 | 2018 | [57496340E03F](<Digital/AU Optronics/AUO332C/57496340E03F>) |
| AU Optronics     | AUO332C | B133XW03 V3      | 1366x768  | 13.0 | 2009 | [E295C9C1B856](<Digital/AU Optronics/AUO332C/E295C9C1B856>) |
| AU Optronics     | AUO333C |                  | 1366x768  | 13.9 | 2013 | [0DCD1DB4227B](<Digital/AU Optronics/AUO333C/0DCD1DB4227B>) |
| AU Optronics     | AUO333C | HPD96            | 1366x768  | 13.9 | 2012 | [F1B004A58862](<Digital/AU Optronics/AUO333C/F1B004A58862>) |
| AU Optronics     | AUO333D |                  | 1920x1080 | 13.9 | 2018 | [87C558ED785C](<Digital/AU Optronics/AUO333D/87C558ED785C>) |
| AU Optronics     | AUO333D |                  | 1920x1080 | 13.9 | 2016 | [973E8C8125B8](<Digital/AU Optronics/AUO333D/973E8C8125B8>) |
| AU Optronics     | AUO335D | B116HAN03.3      | 1920x1080 | 11.6 | 2014 | [125CFB1D2967](<Digital/AU Optronics/AUO335D/125CFB1D2967>) |
| AU Optronics     | AUO3387 | B170PW03 V3      | 1440x900  | 17.2 |      | [258AE1AF03FD](<Digital/AU Optronics/AUO3387/258AE1AF03FD>) |
| AU Optronics     | AUO339F |                  | 1920x1200 | 13.4 | 2021 | [FCBA5CFC7D50](<Digital/AU Optronics/AUO339F/FCBA5CFC7D50>) |
| AU Optronics     | AUO33B7 | B160UANAC.J      | 1920x1200 | 15.9 | 2024 | [A153FC0ABACB](<Digital/AU Optronics/AUO33B7/A153FC0ABACB>) |
| AU Optronics     | AUO33EB |                  | 3840x2160 | 15.3 | 2017 | [D81AADFA82B0](<Digital/AU Optronics/AUO33EB/D81AADFA82B0>) |
| AU Optronics     | AUO33ED |                  | 1920x1080 | 15.3 | 2012 | [7DF7633F47CE](<Digital/AU Optronics/AUO33ED/7DF7633F47CE>) |
| AU Optronics     | AUO3414 | B121EW03 V4      | 1280x800  | 12.0 | 2007 | [54A7DABDF375](<Digital/AU Optronics/AUO3414/54A7DABDF375>) |
| AU Optronics     | AUO342C | B133XW03 V4      | 1366x768  | 13.0 | 2010 | [09CEB08F665A](<Digital/AU Optronics/AUO342C/09CEB08F665A>) |
| AU Optronics     | AUO343C | B140XTN03.4      | 1366x768  | 13.9 | 2012 | [B05C345371C5](<Digital/AU Optronics/AUO343C/B05C345371C5>) |
| AU Optronics     | AUO343D | B140HAK03.4      | 1920x1080 | 13.9 | 2019 | [7E1F5A9F0E01](<Digital/AU Optronics/AUO343D/7E1F5A9F0E01>) |
| AU Optronics     | AUO343D |                  | 1920x1080 | 13.9 | 2016 | [788CF37C0224](<Digital/AU Optronics/AUO343D/788CF37C0224>) |
| AU Optronics     | AUO3479 | G150XTN03.4      | 1024x768  | 14.9 | 2016 | [A468DBD8F649](<Digital/AU Optronics/AUO3479/A468DBD8F649>) |
| AU Optronics     | AUO3487 | B170PW03 V4      | 1440x900  | 17.2 |      | [9A4602CDFD8B](<Digital/AU Optronics/AUO3487/9A4602CDFD8B>) |
| AU Optronics     | AUO348E | B173HAN05.1      | 1920x1080 | 17.3 | 2019 | [10AAA2BE1880](<Digital/AU Optronics/AUO348E/10AAA2BE1880>) |
| AU Optronics     | AUO349F |                  | 3840x2160 | 17.1 | 2021 | [4FA385A4CD34](<Digital/AU Optronics/AUO349F/4FA385A4CD34>) |
| AU Optronics     | AUO34A6 |                  | 1920x1080 | 15.3 | 2022 | [FCDB1FAA7947](<Digital/AU Optronics/AUO34A6/FCDB1FAA7947>) |
| AU Optronics     | AUO34EB | XWHYC            | 3840x2160 | 15.3 | 2018 | [B4DAEE525F1F](<Digital/AU Optronics/AUO34EB/B4DAEE525F1F>) |
| AU Optronics     | AUO34EC |                  | 1366x768  | 15.3 | 2012 | [0EE5C70E22C1](<Digital/AU Optronics/AUO34EC/0EE5C70E22C1>) |
| AU Optronics     | AUO34ED |                  | 1920x1080 | 15.3 | 2012 | [16FA15059263](<Digital/AU Optronics/AUO34ED/16FA15059263>) |
| AU Optronics     | AUO3514 | B121EW03 V5      | 1280x800  | 12.0 | 2007 | [F2EFDAC3BCD6](<Digital/AU Optronics/AUO3514/F2EFDAC3BCD6>) |
| AU Optronics     | AUO352C | B133XW03 V5      | 1366x768  | 13.0 | 2010 | [00E33990E55C](<Digital/AU Optronics/AUO352C/00E33990E55C>) |
| AU Optronics     | AUO353D | B140HAN03.5      | 1920x1080 | 13.9 | 2015 | [8A1990E3C3CF](<Digital/AU Optronics/AUO353D/8A1990E3C3CF>) |
| AU Optronics     | AUO3587 | MW986 +:GQq      | 1440x900  | 17.2 | 2007 | [820B0669D5BA](<Digital/AU Optronics/AUO3587/820B0669D5BA>) |
| AU Optronics     | AUO35AE |                  | 1920x1080 | 17.3 | 2023 | [162C4075FFA6](<Digital/AU Optronics/AUO35AE/162C4075FFA6>) |
| AU Optronics     | AUO35EB | CC53D            | 3840x2160 | 15.3 | 2019 | [13A47F563844](<Digital/AU Optronics/AUO35EB/13A47F563844>) |
| AU Optronics     | AUO35EC | B156XTN03.5      | 1366x768  | 15.3 | 2013 | [0C3732EBEF6A](<Digital/AU Optronics/AUO35EC/0C3732EBEF6A>) |
| AU Optronics     | AUO35EC |                  | 1366x768  | 15.3 | 2012 | [51FCC954AAA0](<Digital/AU Optronics/AUO35EC/51FCC954AAA0>) |
| AU Optronics     | AUO35ED |                  | 1920x1080 | 15.3 | 2013 | [736848D1C04E](<Digital/AU Optronics/AUO35ED/736848D1C04E>) |
| AU Optronics     | AUO3614 | B121EW03 V6      | 1280x800  | 12.0 | 2007 | [35677C9E361F](<Digital/AU Optronics/AUO3614/35677C9E361F>) |
| AU Optronics     | AUO363C | B140XTN03.6      | 1366x768  | 13.9 | 2013 | [186D1CB07BB6](<Digital/AU Optronics/AUO363C/186D1CB07BB6>) |
| AU Optronics     | AUO363D | B140HAN03.6      | 1920x1080 | 13.9 | 2016 | [D59966AA39CF](<Digital/AU Optronics/AUO363D/D59966AA39CF>) |
| AU Optronics     | AUO3691 |                  | 1366x768  | 15.3 | 2020 | [26B4F83DD3C4](<Digital/AU Optronics/AUO3691/26B4F83DD3C4>) |
| AU Optronics     | AUO369F | B156HTN06.2      | 1920x1080 | 15.3 | 2021 | [21A783AEFA2B](<Digital/AU Optronics/AUO369F/21A783AEFA2B>) |
| AU Optronics     | AUO36ED |                  | 1920x1080 | 15.3 | 2014 | [85FA62EEF36E](<Digital/AU Optronics/AUO36ED/85FA62EEF36E>) |
| AU Optronics     | AUO36ED | B156HTN03.6      | 1920x1080 | 15.3 | 2013 | [751F4AF4F589](<Digital/AU Optronics/AUO36ED/751F4AF4F589>) |
| AU Optronics     | AUO3714 | B121EW03 V7      | 1280x800  | 12.0 | 2007 | [60F554BBDA53](<Digital/AU Optronics/AUO3714/60F554BBDA53>) |
| AU Optronics     | AUO373C |                  | 1366x768  | 13.9 | 2013 | [111335F81346](<Digital/AU Optronics/AUO373C/111335F81346>) |
| AU Optronics     | AUO373D |                  | 1920x1080 | 13.9 | 2016 | [7CDB16846F33](<Digital/AU Optronics/AUO373D/7CDB16846F33>) |
| AU Optronics     | AUO3787 | WR542 ):HQr      | 1440x900  | 17.2 | 2007 | [72F237ED85E8](<Digital/AU Optronics/AUO3787/72F237ED85E8>) |
| AU Optronics     | AUO3791 |                  | 1920x1080 | 15.3 | 2020 | [E0317419EEFB](<Digital/AU Optronics/AUO3791/E0317419EEFB>) |
| AU Optronics     | AUO37AC |                  | 1920x1200 | 14.0 | 2023 | [6A0597D9927B](<Digital/AU Optronics/AUO37AC/6A0597D9927B>) |
| AU Optronics     | AUO37AD |                  | 1920x1200 | 15.9 | 2023 | [871FD405114B](<Digital/AU Optronics/AUO37AD/871FD405114B>) |
| AU Optronics     | AUO37ED | B156HTN03.7      | 1920x1080 | 15.3 | 2013 | [51009D76E0F5](<Digital/AU Optronics/AUO37ED/51009D76E0F5>) |
| AU Optronics     | AUO3814 | B121EW03 V8      | 1280x800  | 12.0 | 2007 | [DAFDE9F272BA](<Digital/AU Optronics/AUO3814/DAFDE9F272BA>) |
| AU Optronics     | AUO383D | B140HAN03.8      | 1920x1080 | 13.9 | 2016 | [046AC8DE6BE3](<Digital/AU Optronics/AUO383D/046AC8DE6BE3>) |
| AU Optronics     | AUO3892 | 5NG4M            | 1920x1080 | 15.3 | 2020 | [A6B98F5FC015](<Digital/AU Optronics/AUO3892/A6B98F5FC015>) |
| AU Optronics     | AUO38A9 |                  | 2560x1600 | 15.9 | 2022 | [B6F5E12B1F45](<Digital/AU Optronics/AUO38A9/B6F5E12B1F45>) |
| AU Optronics     | AUO38ED |                  | 1920x1080 | 15.3 | 2017 | [B894A2ACDA54](<Digital/AU Optronics/AUO38ED/B894A2ACDA54>) |
| AU Optronics     | AUO38ED |                  | 1920x1080 | 15.3 | 2016 | [074E4388811D](<Digital/AU Optronics/AUO38ED/074E4388811D>) |
| AU Optronics     | AUO38ED |                  | 1920x1080 | 15.3 | 2015 | [0BEE2F64EA3C](<Digital/AU Optronics/AUO38ED/0BEE2F64EA3C>) |
| AU Optronics     | AUO38ED | B156HTN03.8      | 1920x1080 | 15.3 | 2014 | [571ED680F933](<Digital/AU Optronics/AUO38ED/571ED680F933>) |
| AU Optronics     | AUO3914 | B121EW03 V9      | 1280x800  | 12.0 | 2007 | [01BBBB3C9E45](<Digital/AU Optronics/AUO3914/01BBBB3C9E45>) |
| AU Optronics     | AUO393C | B140XTN03.9      | 1366x768  | 13.9 | 2015 | [4B47613DE554](<Digital/AU Optronics/AUO393C/4B47613DE554>) |
| AU Optronics     | AUO393D | YRMG8            | 1920x1080 | 13.9 | 2018 | [DDFF7B496FA1](<Digital/AU Optronics/AUO393D/DDFF7B496FA1>) |
| AU Optronics     | AUO39A4 |                  | 3840x2160 | 15.3 | 2022 | [2923C114A363](<Digital/AU Optronics/AUO39A4/2923C114A363>) |
| AU Optronics     | AUO39ED |                  | 1920x1080 | 15.3 | 2018 | [570DA1780BB8](<Digital/AU Optronics/AUO39ED/570DA1780BB8>) |
| AU Optronics     | AUO39ED | B156HTN03.9      | 1920x1080 | 15.3 | 2014 | [C56C2CF78611](<Digital/AU Optronics/AUO39ED/C56C2CF78611>) |
| AU Optronics     | AUO3A8C |                  | 1920x1080 | 13.2 | 2019 | [0FE88B609523](<Digital/AU Optronics/AUO3A8C/0FE88B609523>) |
| AU Optronics     | AUO3A94 | B173RTN03.0      | 1600x900  | 17.3 | 2020 | [E996F48BDF1A](<Digital/AU Optronics/AUO3A94/E996F48BDF1A>) |
| AU Optronics     | AUO3B3C | B140XTN03.B      | 1366x768  | 13.9 | 2017 | [6AB0701597D0](<Digital/AU Optronics/AUO3B3C/6AB0701597D0>) |
| AU Optronics     | AUO3B3D |                  | 1920x1080 | 13.9 | 2017 | [3D5EA0D7DED1](<Digital/AU Optronics/AUO3B3D/3D5EA0D7DED1>) |
| AU Optronics     | AUO3B44 | GM521 '5AHf      | 1280x800  | 14.0 | 2006 | [6317A4FD8AD5](<Digital/AU Optronics/AUO3B44/6317A4FD8AD5>) |
| AU Optronics     | AUO3B9C |                  | 1920x1080 | 15.3 | 2021 | [CA88A0285E23](<Digital/AU Optronics/AUO3B9C/CA88A0285E23>) |
| AU Optronics     | AUO3C9B | B170QAN01.0      | 2560x1600 | 17.2 | 2021 | [AFC2E5FDF3FF](<Digital/AU Optronics/AUO3C9B/AFC2E5FDF3FF>) |
| AU Optronics     | AUO3CA2 | RHJNF            | 2560x1600 | 15.9 | 2022 | [1FBAF7F32DE3](<Digital/AU Optronics/AUO3CA2/1FBAF7F32DE3>) |
| AU Optronics     | AUO3CAD |                  | 1920x1200 | 14.0 | 2023 | [15C0A51209EF](<Digital/AU Optronics/AUO3CAD/15C0A51209EF>) |
| AU Optronics     | AUO3DA3 |                  | 1920x1080 | 15.3 | 2021 | [0858CDBCA039](<Digital/AU Optronics/AUO3DA3/0858CDBCA039>) |
| AU Optronics     | AUO3E3D | B140HAN03.E      | 1920x1080 | 13.9 | 2017 | [32F7E312C74E](<Digital/AU Optronics/AUO3E3D/32F7E312C74E>) |
| AU Optronics     | AUO3F3D | XNMP0            | 1920x1080 | 13.9 | 2019 | [672338CE889D](<Digital/AU Optronics/AUO3F3D/672338CE889D>) |
| AU Optronics     | AUO402C | B133XW04 V0      | 1366x768  | 13.0 | 2010 | [412698B28E81](<Digital/AU Optronics/AUO402C/412698B28E81>) |
| AU Optronics     | AUO402D | B133HAN04.0      | 1920x1080 | 13.2 | 2015 | [117DC97FCA09](<Digital/AU Optronics/AUO402D/117DC97FCA09>) |
| AU Optronics     | AUO403C | B140XW04 V0      | 1366x768  | 13.9 | 2010 | [386C4B44712E](<Digital/AU Optronics/AUO403C/386C4B44712E>) |
| AU Optronics     | AUO403D | B140HAB04.0      | 1920x1080 | 13.9 | 2020 | [EC138FC2FC95](<Digital/AU Optronics/AUO403D/EC138FC2FC95>) |
| AU Optronics     | AUO403D |                  | 1920x1080 | 13.9 | 2019 | [9EC14BDAC78D](<Digital/AU Optronics/AUO403D/9EC14BDAC78D>) |
| AU Optronics     | AUO403D | B140HAN04.0      | 1920x1080 | 13.9 | 2018 | [023FA473395D](<Digital/AU Optronics/AUO403D/023FA473395D>) |
| AU Optronics     | AUO403D | B140HAN04.0      | 1920x1080 | 13.9 | 2017 | [F53E51906963](<Digital/AU Optronics/AUO403D/F53E51906963>) |
| AU Optronics     | AUO403D | B140HAN04.0      | 1920x1080 | 13.9 | 2016 | [2859A0B818BC](<Digital/AU Optronics/AUO403D/2859A0B818BC>) |
| AU Optronics     | AUO4047 | GX968            | 1440x900  | 14.0 | 2007 | [BF80957C2699](<Digital/AU Optronics/AUO4047/BF80957C2699>) |
| AU Optronics     | AUO405C | B116XAK01.0      | 1366x768  | 11.6 | 2016 | [36527300981E](<Digital/AU Optronics/AUO405C/36527300981E>) |
| AU Optronics     | AUO405C | 0K7CX            | 1366x768  | 11.6 | 2015 | [04692F557DA4](<Digital/AU Optronics/AUO405C/04692F557DA4>) |
| AU Optronics     | AUO405C | 0MMWN            | 1366x768  | 11.6 | 2013 | [9E2ACB2EB7FF](<Digital/AU Optronics/AUO405C/9E2ACB2EB7FF>) |
| AU Optronics     | AUO405C | B116XTN04.0      | 1366x768  | 11.6 | 2012 | [A1707E3AD255](<Digital/AU Optronics/AUO405C/A1707E3AD255>) |
| AU Optronics     | AUO4087 |                  | 1440x900  | 17.2 | 2005 | [A830F8B57528](<Digital/AU Optronics/AUO4087/A830F8B57528>) |
| AU Optronics     | AUO408D | B140HAN04.E      | 1920x1080 | 13.9 | 2019 | [4BFAD2B09022](<Digital/AU Optronics/AUO408D/4BFAD2B09022>) |
| AU Optronics     | AUO409D | B173HAN04.0      | 1920x1080 | 17.3 | 2018 | [14E6162FDC95](<Digital/AU Optronics/AUO409D/14E6162FDC95>) |
| AU Optronics     | AUO40A3 | J46WR            | 2560x1600 | 14.0 | 2022 | [F8CD7E526A30](<Digital/AU Optronics/AUO40A3/F8CD7E526A30>) |
| AU Optronics     | AUO40B0 |                  | 1920x1080 | 21.1 | 2015 | [A76CB70E0A79](<Digital/AU Optronics/AUO40B0/A76CB70E0A79>) |
| AU Optronics     | AUO40EC | W64C6            | 1366x768  | 15.3 | 2013 | [23540BABC7CD](<Digital/AU Optronics/AUO40EC/23540BABC7CD>) |
| AU Optronics     | AUO40EC | B156XW04 V0      | 1366x768  | 15.3 | 2009 | [0024E2EAD592](<Digital/AU Optronics/AUO40EC/0024E2EAD592>) |
| AU Optronics     | AUO40EC | W64C6            | 1366x768  | 15.3 |      | [FA2E70804C48](<Digital/AU Optronics/AUO40EC/FA2E70804C48>) |
| AU Optronics     | AUO40ED |                  | 1920x1080 | 15.3 | 2015 | [B3C1216A3DF3](<Digital/AU Optronics/AUO40ED/B3C1216A3DF3>) |
| AU Optronics     | AUO4100 | AUO^ B101UAN01.C | 1920x1200 | 10.3 | 2013 | [2EDA34E7BB6A](<Digital/AU Optronics/AUO4100/2EDA34E7BB6A>) |
| AU Optronics     | AUO412C | B133XW04 V1      | 1366x768  | 13.0 | 2010 | [42863D6F0BAB](<Digital/AU Optronics/AUO412C/42863D6F0BAB>) |
| AU Optronics     | AUO412D | B133HAN04.1      | 1920x1080 | 13.2 | 2015 | [426856FA3C8A](<Digital/AU Optronics/AUO412D/426856FA3C8A>) |
| AU Optronics     | AUO413D |                  | 1920x1080 | 13.9 | 2019 | [8A9DFE75E689](<Digital/AU Optronics/AUO413D/8A9DFE75E689>) |
| AU Optronics     | AUO413D |                  | 1920x1080 | 13.9 | 2016 | [CAA8EDBC8490](<Digital/AU Optronics/AUO413D/CAA8EDBC8490>) |
| AU Optronics     | AUO4147 | DV5J1            | 1440x900  | 14.0 | 2009 | [53A6B8BFCE2A](<Digital/AU Optronics/AUO4147/53A6B8BFCE2A>) |
| AU Optronics     | AUO418D | B140HAK02.6      | 1920x1080 | 13.9 | 2019 | [61A55A46973F](<Digital/AU Optronics/AUO418D/61A55A46973F>) |
| AU Optronics     | AUO4195 |                  | 2560x1600 | 13.4 | 2020 | [94A92C4B7B79](<Digital/AU Optronics/AUO4195/94A92C4B7B79>) |
| AU Optronics     | AUO4199 | 61FT0            | 1920x1080 | 15.3 | 2021 | [6FBC33D10034](<Digital/AU Optronics/AUO4199/6FBC33D10034>) |
| AU Optronics     | AUO41A2 | B173ZAN06.C      | 3840x2160 | 17.1 | 2022 | [50B56223BD59](<Digital/AU Optronics/AUO41A2/50B56223BD59>) |
| AU Optronics     | AUO41EB | HY6NC            | 3840x2160 | 15.3 | 2019 | [93F2056D50B2](<Digital/AU Optronics/AUO41EB/93F2056D50B2>) |
| AU Optronics     | AUO41EB | 7X71H            | 3840x2160 | 15.3 | 2018 | [45FA67DF2D2D](<Digital/AU Optronics/AUO41EB/45FA67DF2D2D>) |
| AU Optronics     | AUO41EC | B156XTN04.1      | 1366x768  | 15.3 | 2013 | [B1B6AC8292FF](<Digital/AU Optronics/AUO41EC/B1B6AC8292FF>) |
| AU Optronics     | AUO41EC | B156XW04 V1      | 1366x768  | 15.3 | 2009 | [BCD92AF1784A](<Digital/AU Optronics/AUO41EC/BCD92AF1784A>) |
| AU Optronics     | AUO41ED | B156HAN04.1      | 1920x1080 | 15.3 | 2016 | [14F64FFF3966](<Digital/AU Optronics/AUO41ED/14F64FFF3966>) |
| AU Optronics     | AUO41ED |                  | 1920x1080 | 15.3 | 2015 | [4B8768CBFA70](<Digital/AU Optronics/AUO41ED/4B8768CBFA70>) |
| AU Optronics     | AUO4214 | Y164G            | 1280x800  | 12.0 | 2007 | [65AC362D7D49](<Digital/AU Optronics/AUO4214/65AC362D7D49>) |
| AU Optronics     | AUO422D |                  | 1920x1080 | 13.2 | 2016 | [4228EB9D9803](<Digital/AU Optronics/AUO422D/4228EB9D9803>) |
| AU Optronics     | AUO423D | B140HAN04.2      | 1920x1080 | 13.9 | 2016 | [1B27ACFFC84D](<Digital/AU Optronics/AUO423D/1B27ACFFC84D>) |
| AU Optronics     | AUO4277 | WP576            | 1440x900  | 15.4 | 2007 | [01625BA94496](<Digital/AU Optronics/AUO4277/01625BA94496>) |
| AU Optronics     | AUO429D | 1WK6C            | 1920x1080 | 17.3 | 2019 | [4C91D3B8DB3D](<Digital/AU Optronics/AUO429D/4C91D3B8DB3D>) |
| AU Optronics     | AUO429D | B173HAN04.2      | 1920x1080 | 17.3 | 2018 | [13621A1DECAC](<Digital/AU Optronics/AUO429D/13621A1DECAC>) |
| AU Optronics     | AUO42EB | B156ZAN04.2      | 3840x2160 | 15.3 | 2018 | [F726DCFD0007](<Digital/AU Optronics/AUO42EB/F726DCFD0007>) |
| AU Optronics     | AUO42EC | B156XTN04.2      | 1366x768  | 15.3 | 2013 | [6D95C8323CFA](<Digital/AU Optronics/AUO42EC/6D95C8323CFA>) |
| AU Optronics     | AUO42ED |                  | 1920x1080 | 15.3 | 2017 | [85376F7D72DA](<Digital/AU Optronics/AUO42ED/85376F7D72DA>) |
| AU Optronics     | AUO433D | TC3NM            | 1920x1080 | 13.9 | 2017 | [70565D39B232](<Digital/AU Optronics/AUO433D/70565D39B232>) |
| AU Optronics     | AUO4344 | B141EW04 V3      | 1280x800  | 14.0 | 2006 | [49F00A5BDDCD](<Digital/AU Optronics/AUO4344/49F00A5BDDCD>) |
| AU Optronics     | AUO435C | B116XAN04.3      | 1366x768  | 11.6 | 2016 | [A233A4242902](<Digital/AU Optronics/AUO435C/A233A4242902>) |
| AU Optronics     | AUO439D | B173HAN04.3      | 1920x1080 | 17.3 | 2018 | [09563A32EC09](<Digital/AU Optronics/AUO439D/09563A32EC09>) |
| AU Optronics     | AUO43AD |                  | 1920x1200 | 14.0 | 2023 | [7000A415469F](<Digital/AU Optronics/AUO43AD/7000A415469F>) |
| AU Optronics     | AUO43EC | B156XTN04.3      | 1366x768  | 15.3 | 2013 | [94001837F703](<Digital/AU Optronics/AUO43EC/94001837F703>) |
| AU Optronics     | AUO43ED | B156HAN04.3      | 1920x1080 | 15.3 | 2016 | [3F9E8E25B5AC](<Digital/AU Optronics/AUO43ED/3F9E8E25B5AC>) |
| AU Optronics     | AUO442D | B133HAN04.4      | 1920x1080 | 13.2 | 2016 | [917617F46C80](<Digital/AU Optronics/AUO442D/917617F46C80>) |
| AU Optronics     | AUO4444 | B141EW04 V4      | 1280x800  | 14.0 | 2006 | [2D2138E809D5](<Digital/AU Optronics/AUO4444/2D2138E809D5>) |
| AU Optronics     | AUO449D | 5YKTJ            | 1920x1080 | 17.3 | 2019 | [7D77BF8AE006](<Digital/AU Optronics/AUO449D/7D77BF8AE006>) |
| AU Optronics     | AUO449D | B173HAN04.4      | 1920x1080 | 17.3 | 2018 | [462470CBD811](<Digital/AU Optronics/AUO449D/462470CBD811>) |
| AU Optronics     | AUO449D | B173HAN04        | 1920x1080 | 17.3 |      | [A8F4822825FD](<Digital/AU Optronics/AUO449D/A8F4822825FD>) |
| AU Optronics     | AUO44EC | B156XTN04.4      | 1366x768  | 15.3 | 2013 | [00BFA0297364](<Digital/AU Optronics/AUO44EC/00BFA0297364>) |
| AU Optronics     | AUO44ED | B156HAN04.4      | 1920x1080 | 15.3 | 2016 | [C557CDECB69F](<Digital/AU Optronics/AUO44ED/C557CDECB69F>) |
| AU Optronics     | AUO453D | N4HYV            | 1920x1080 | 13.9 | 2018 | [D424816DE76B](<Digital/AU Optronics/AUO453D/D424816DE76B>) |
| AU Optronics     | AUO4544 | WP948            | 1280x800  | 14.0 | 2008 | [35BF31DFD84B](<Digital/AU Optronics/AUO4544/35BF31DFD84B>) |
| AU Optronics     | AUO4544 | B141EW04 V5      | 1280x800  | 14.0 | 2007 | [6A593D7E1BAB](<Digital/AU Optronics/AUO4544/6A593D7E1BAB>) |
| AU Optronics     | AUO4544 | TK033 2GV]       | 1280x800  | 14.0 | 2006 | [A5A990D9117F](<Digital/AU Optronics/AUO4544/A5A990D9117F>) |
| AU Optronics     | AUO4599 | MCX7D            | 1920x1080 | 15.3 | 2021 | [9F74341A5467](<Digital/AU Optronics/AUO4599/9F74341A5467>) |
| AU Optronics     | AUO459D | B160UAN03.3      | 1920x1200 | 15.9 | 2022 | [1327FF0A8950](<Digital/AU Optronics/AUO459D/1327FF0A8950>) |
| AU Optronics     | AUO459D | B160UAN03.3      | 1920x1200 | 15.9 | 2021 | [1F991FC78773](<Digital/AU Optronics/AUO459D/1F991FC78773>) |
| AU Optronics     | AUO45A1 |                  | 1920x1200 | 14.0 | 2021 | [7E9386D3DA8D](<Digital/AU Optronics/AUO45A1/7E9386D3DA8D>) |
| AU Optronics     | AUO45A8 | B180QAN01.2      | 2560x1600 | 18.0 | 2022 | [3377AFBAFE55](<Digital/AU Optronics/AUO45A8/3377AFBAFE55>) |
| AU Optronics     | AUO45B2 | KFV6C            | 1920x1200 | 14.0 | 2024 | [CF5BE1EB32EC](<Digital/AU Optronics/AUO45B2/CF5BE1EB32EC>) |
| AU Optronics     | AUO45EC | 3XJ36            | 1366x768  | 15.3 | 2015 | [8923E66A0238](<Digital/AU Optronics/AUO45EC/8923E66A0238>) |
| AU Optronics     | AUO45EC |                  | 1366x768  | 15.3 | 2013 | [15E2B2822029](<Digital/AU Optronics/AUO45EC/15E2B2822029>) |
| AU Optronics     | AUO45EC |                  | 1366x768  | 15.3 | 2011 | [17E34B0A710B](<Digital/AU Optronics/AUO45EC/17E34B0A710B>) |
| AU Optronics     | AUO45EC | B156XW04 V5      | 1366x768  | 15.3 | 2010 | [871DF12F4604](<Digital/AU Optronics/AUO45EC/871DF12F4604>) |
| AU Optronics     | AUO45ED | B156HAN04.5      | 1920x1080 | 15.3 | 2017 | [4DF7311454DE](<Digital/AU Optronics/AUO45ED/4DF7311454DE>) |
| AU Optronics     | AUO462D | F7VDJ            | 1920x1080 | 13.2 | 2016 | [00F59D80F218](<Digital/AU Optronics/AUO462D/00F59D80F218>) |
| AU Optronics     | AUO463D | B140HAN04.6      | 1920x1080 | 13.9 | 2018 | [D4BC406BA112](<Digital/AU Optronics/AUO463D/D4BC406BA112>) |
| AU Optronics     | AUO463D | F87J3            | 1920x1080 | 13.9 |      | [C8D6E1541720](<Digital/AU Optronics/AUO463D/C8D6E1541720>) |
| AU Optronics     | AUO4644 | RU207 )8ENm      | 1280x800  | 14.0 | 2006 | [5054CA9249A3](<Digital/AU Optronics/AUO4644/5054CA9249A3>) |
| AU Optronics     | AUO4644 | CY672            | 1280x800  | 14.0 |      | [52FDB77F0E1E](<Digital/AU Optronics/AUO4644/52FDB77F0E1E>) |
| AU Optronics     | AUO46EC | B156XTN04.6      | 1366x768  | 15.3 | 2015 | [D6C67F873AB4](<Digital/AU Optronics/AUO46EC/D6C67F873AB4>) |
| AU Optronics     | AUO46EC |                  | 1366x768  | 15.3 | 2013 | [EFCE199979BC](<Digital/AU Optronics/AUO46EC/EFCE199979BC>) |
| AU Optronics     | AUO46EC |                  | 1366x768  | 15.3 | 2011 | [4AF4BC481188](<Digital/AU Optronics/AUO46EC/4AF4BC481188>) |
| AU Optronics     | AUO46EC | B156XW04 V6      | 1366x768  | 15.3 | 2010 | [AD11712F3099](<Digital/AU Optronics/AUO46EC/AD11712F3099>) |
| AU Optronics     | AUO46EC | B156XTN04        | 1366x768  | 15.3 |      | [EEBBA859E9C1](<Digital/AU Optronics/AUO46EC/EEBBA859E9C1>) |
| AU Optronics     | AUO472D |                  | 1920x1080 | 13.2 | 2017 | [260442373662](<Digital/AU Optronics/AUO472D/260442373662>) |
| AU Optronics     | AUO4792 |                  | 1366x768  | 13.9 | 2020 | [53B88A1C665C](<Digital/AU Optronics/AUO4792/53B88A1C665C>) |
| AU Optronics     | AUO4799 |                  | 1920x1080 | 15.3 | 2021 | [97474BD75037](<Digital/AU Optronics/AUO4799/97474BD75037>) |
| AU Optronics     | AUO479D | B173HAN04.7      | 1920x1080 | 17.3 | 2019 | [CC1136699E4C](<Digital/AU Optronics/AUO479D/CC1136699E4C>) |
| AU Optronics     | AUO47EC | B156XW004.7      | 1366x768  | 15.3 | 2013 | [2B5ABB1FE8C1](<Digital/AU Optronics/AUO47EC/2B5ABB1FE8C1>) |
| AU Optronics     | AUO47EC |                  | 1366x768  | 11.6 | 2012 | [3054701BAF6A](<Digital/AU Optronics/AUO47EC/3054701BAF6A>) |
| AU Optronics     | AUO47EC |                  | 1366x768  | 15.3 | 2012 | [D57E308F8B97](<Digital/AU Optronics/AUO47EC/D57E308F8B97>) |
| AU Optronics     | AUO482D |                  | 1920x1080 | 13.2 | 2017 | [AB716E21DD61](<Digital/AU Optronics/AUO482D/AB716E21DD61>) |
| AU Optronics     | AUO489D | 5Y1DR            | 1920x1080 | 17.1 | 2019 | [FDA8E55D65DD](<Digital/AU Optronics/AUO489D/FDA8E55D65DD>) |
| AU Optronics     | AUO48A3 | 49NVT            | 1920x1200 | 13.4 | 2021 | [715FF754D711](<Digital/AU Optronics/AUO48A3/715FF754D711>) |
| AU Optronics     | AUO48B0 |                  | 2240x1400 | 14.0 | 2023 | [27BA827F2F9D](<Digital/AU Optronics/AUO48B0/27BA827F2F9D>) |
| AU Optronics     | AUO48EC | B156XW004.8      | 1366x768  | 15.3 | 2013 | [0F0F23090608](<Digital/AU Optronics/AUO48EC/0F0F23090608>) |
| AU Optronics     | AUO492D | B133HAN04.9      | 1920x1080 | 13.2 | 2017 | [1643AE7109E7](<Digital/AU Optronics/AUO492D/1643AE7109E7>) |
| AU Optronics     | AUO4995 |                  | 3840x2160 | 13.9 | 2019 | [1EF9D48CF266](<Digital/AU Optronics/AUO4995/1EF9D48CF266>) |
| AU Optronics     | AUO4999 | B156HAN02.1      | 1920x1080 | 15.3 | 2019 | [2DEA45C82945](<Digital/AU Optronics/AUO4999/2DEA45C82945>) |
| AU Optronics     | AUO499A | X7F7W            | 2560x1600 | 14.0 | 2021 | [F0BB995F06A4](<Digital/AU Optronics/AUO499A/F0BB995F06A4>) |
| AU Optronics     | AUO499F |                  | 1920x1080 | 15.3 | 2021 | [6A40ED52B9AD](<Digital/AU Optronics/AUO499F/6A40ED52B9AD>) |
| AU Optronics     | AUO4A2D |                  | 1920x1080 | 13.2 | 2017 | [7C2F9E9CDB0B](<Digital/AU Optronics/AUO4A2D/7C2F9E9CDB0B>) |
| AU Optronics     | AUO4A90 | 3477W            | 1920x1080 | 13.9 | 2020 | [30A7743CA236](<Digital/AU Optronics/AUO4A90/30A7743CA236>) |
| AU Optronics     | AUO4A99 | B156HAN02.1      | 1920x1080 | 15.3 | 2021 | [3AE5400D247F](<Digital/AU Optronics/AUO4A99/3AE5400D247F>) |
| AU Optronics     | AUO4B2D |                  | 1920x1080 | 13.2 | 2020 | [CD0620F2B783](<Digital/AU Optronics/AUO4B2D/CD0620F2B783>) |
| AU Optronics     | AUO4B2D |                  | 1920x1080 | 13.2 | 2019 | [69C8C7B0F6C7](<Digital/AU Optronics/AUO4B2D/69C8C7B0F6C7>) |
| AU Optronics     | AUO4B2D |                  | 1920x1080 | 13.2 | 2018 | [ABB1CEDEC2C3](<Digital/AU Optronics/AUO4B2D/ABB1CEDEC2C3>) |
| AU Optronics     | AUO4B98 |                  | 1920x1200 | 13.4 | 2021 | [D5705F339821](<Digital/AU Optronics/AUO4B98/D5705F339821>) |
| AU Optronics     | AUO4B9D | B173HAN04.9      | 1920x1080 | 17.3 | 2020 | [9977A9E97FEF](<Digital/AU Optronics/AUO4B9D/9977A9E97FEF>) |
| AU Optronics     | AUO4CA6 |                  | 1366x768  | 15.3 | 2022 | [366ED5B1F75B](<Digital/AU Optronics/AUO4CA6/366ED5B1F75B>) |
| AU Optronics     | AUO4DA6 |                  | 1920x1200 | 15.9 | 2022 | [401DE8309EB2](<Digital/AU Optronics/AUO4DA6/401DE8309EB2>) |
| AU Optronics     | AUO4E8B |                  | 1920x1080 | 13.2 | 2020 | [EF6BD326A37D](<Digital/AU Optronics/AUO4E8B/EF6BD326A37D>) |
| AU Optronics     | AUO4E8D |                  | 1920x1080 | 15.3 | 2018 | [DCBE542B16DF](<Digital/AU Optronics/AUO4E8D/DCBE542B16DF>) |
| AU Optronics     | AUO4F8A |                  | 1920x1080 | 13.9 | 2019 | [0C3AA1B039B6](<Digital/AU Optronics/AUO4F8A/0C3AA1B039B6>) |
| AU Optronics     | AUO4F9B | X6NRM            | 2560x1600 | 14.0 | 2021 | [4E5AB870C55E](<Digital/AU Optronics/AUO4F9B/4E5AB870C55E>) |
| AU Optronics     | AUO5024 | FM736            | 1280x800  | 13.4 | 2008 | [2BF1069A2BA7](<Digital/AU Optronics/AUO5024/2BF1069A2BA7>) |
| AU Optronics     | AUO502D | RN5TT            | 1920x1080 | 13.0 | 2017 | [DB55D7923DAF](<Digital/AU Optronics/AUO502D/DB55D7923DAF>) |
| AU Optronics     | AUO503D | D04YD            | 1920x1080 | 13.9 | 2017 | [066DA5479F19](<Digital/AU Optronics/AUO503D/066DA5479F19>) |
| AU Optronics     | AUO5044 | B141EW05 V0      | 1280x800  | 14.0 | 2007 | [3FB6F3520C9C](<Digital/AU Optronics/AUO5044/3FB6F3520C9C>) |
| AU Optronics     | AUO505C | B116XAN05.0      | 1366x768  | 11.6 | 2015 | [818C4E015E0E](<Digital/AU Optronics/AUO505C/818C4E015E0E>) |
| AU Optronics     | AUO505D |                  | 1920x1080 | 11.6 | 2017 | [F6C9E9E4C119](<Digital/AU Optronics/AUO505D/F6C9E9E4C119>) |
| AU Optronics     | AUO505D | B116HAN05.0      | 1920x1080 | 11.6 | 2014 | [EF333DE0393D](<Digital/AU Optronics/AUO505D/EF333DE0393D>) |
| AU Optronics     | AUO5090 |                  | 1366x768  | 13.2 | 2020 | [21A0D26BA0E8](<Digital/AU Optronics/AUO5090/21A0D26BA0E8>) |
| AU Optronics     | AUO509D | B173HAN05.0      | 1920x1080 | 17.3 | 2019 | [108C7E364308](<Digital/AU Optronics/AUO509D/108C7E364308>) |
| AU Optronics     | AUO509D | B173HAN05        | 1920x1080 | 17.3 |      | [7BC3E6245DE3](<Digital/AU Optronics/AUO509D/7BC3E6245DE3>) |
| AU Optronics     | AUO50D4 |                  | 1280x800  | 10.3 | 2010 | [23790316B2E7](<Digital/AU Optronics/AUO50D4/23790316B2E7>) |
| AU Optronics     | AUO512D | B133HAN05.1      | 1920x1080 | 13.2 | 2018 | [451AAA427FDB](<Digital/AU Optronics/AUO512D/451AAA427FDB>) |
| AU Optronics     | AUO513D | B140HAN05.1      | 1920x1080 | 13.9 | 2017 | [4DB6D6C5DB3E](<Digital/AU Optronics/AUO513D/4DB6D6C5DB3E>) |
| AU Optronics     | AUO5144 | B141EW05 V1      | 1280x800  | 14.0 | 2007 | [E562C0B54E81](<Digital/AU Optronics/AUO5144/E562C0B54E81>) |
| AU Optronics     | AUO515C | B116XAN05        | 1366x768  | 11.6 |      | [C0AEBB16AFCF](<Digital/AU Optronics/AUO515C/C0AEBB16AFCF>) |
| AU Optronics     | AUO518B |                  | 1920x1080 | 13.2 | 2019 | [BD07257550D9](<Digital/AU Optronics/AUO518B/BD07257550D9>) |
| AU Optronics     | AUO5191 |                  | 1366x768  | 15.3 | 2020 | [DA80B889652B](<Digital/AU Optronics/AUO5191/DA80B889652B>) |
| AU Optronics     | AUO519D |                  | 1920x1080 | 17.3 | 2020 | [9F6582012A8B](<Digital/AU Optronics/AUO519D/9F6582012A8B>) |
| AU Optronics     | AUO519D | B173HAN05.1      | 1920x1080 | 17.3 | 2019 | [D9EECE4621DB](<Digital/AU Optronics/AUO519D/D9EECE4621DB>) |
| AU Optronics     | AUO51EB |                  | 3840x2160 | 15.3 | 2019 | [71B987F3A4F0](<Digital/AU Optronics/AUO51EB/71B987F3A4F0>) |
| AU Optronics     | AUO51ED | HPJGK            | 1920x1080 | 15.3 |      | [6FB669607C3C](<Digital/AU Optronics/AUO51ED/6FB669607C3C>) |
| AU Optronics     | AUO522D | 2DK4K            | 1920x1080 | 13.2 | 2018 | [18AEA4F61B8C](<Digital/AU Optronics/AUO522D/18AEA4F61B8C>) |
| AU Optronics     | AUO522D |                  | 1920x1080 | 13.2 | 2017 | [A6514AFDF8A9](<Digital/AU Optronics/AUO522D/A6514AFDF8A9>) |
| AU Optronics     | AUO523D | NP5R3            | 1920x1080 | 13.9 | 2017 | [A1665D2C25D2](<Digital/AU Optronics/AUO523D/A1665D2C25D2>) |
| AU Optronics     | AUO52ED | B156HTN05.2      | 1920x1080 | 15.3 | 2016 | [42B4D974D1A6](<Digital/AU Optronics/AUO52ED/42B4D974D1A6>) |
| AU Optronics     | AUO533D |                  | 1920x1080 | 13.9 | 2017 | [B2C4AECAC58B](<Digital/AU Optronics/AUO533D/B2C4AECAC58B>) |
| AU Optronics     | AUO5344 | C384H            | 1280x800  | 14.0 | 2008 | [1F532EAA40A8](<Digital/AU Optronics/AUO5344/1F532EAA40A8>) |
| AU Optronics     | AUO53AB | B173HAN04.9      | 1920x1080 | 17.3 | 2023 | [0A329EE8CB26](<Digital/AU Optronics/AUO53AB/0A329EE8CB26>) |
| AU Optronics     | AUO53AD |                  | 1920x1200 | 13.4 | 2022 | [59BABC8AE76B](<Digital/AU Optronics/AUO53AD/59BABC8AE76B>) |
| AU Optronics     | AUO53D4 | B101EW05 V3      | 1280x800  | 10.3 | 2010 | [CF3C337B1E73](<Digital/AU Optronics/AUO53D4/CF3C337B1E73>) |
| AU Optronics     | AUO53ED | B156HTN05.3      | 1920x1080 | 15.3 | 2016 | [13F0C0469FAC](<Digital/AU Optronics/AUO53ED/13F0C0469FAC>) |
| AU Optronics     | AUO543D |                  | 1920x1080 | 13.9 | 2017 | [6E6F58FCB894](<Digital/AU Optronics/AUO543D/6E6F58FCB894>) |
| AU Optronics     | AUO5491 | D5MVF            | 1920x1080 | 13.9 | 2020 | [10374FE80F6E](<Digital/AU Optronics/AUO5491/10374FE80F6E>) |
| AU Optronics     | AUO54B0 | B160QAN02.N      | 2560x1600 | 15.9 | 2021 | [BFD1011397A3](<Digital/AU Optronics/AUO54B0/BFD1011397A3>) |
| AU Optronics     | AUO552D |                  | 1920x1080 | 13.2 | 2017 | [6360D58AFEEC](<Digital/AU Optronics/AUO552D/6360D58AFEEC>) |
| AU Optronics     | AUO553D | B140HAN05.5      | 1920x1080 | 13.9 | 2018 | [D986CF7E8A7F](<Digital/AU Optronics/AUO553D/D986CF7E8A7F>) |
| AU Optronics     | AUO5544 | 44P64            | 1280x800  | 14.0 | 2010 | [48704DCAFADB](<Digital/AU Optronics/AUO5544/48704DCAFADB>) |
| AU Optronics     | AUO559C |                  | 1920x1080 | 13.9 | 2021 | [06BD6C35932A](<Digital/AU Optronics/AUO559C/06BD6C35932A>) |
| AU Optronics     | AUO562D | 84XF7            | 1920x1080 | 13.2 | 2018 | [3E25C52BA13D](<Digital/AU Optronics/AUO562D/3E25C52BA13D>) |
| AU Optronics     | AUO563D | YCMTV            | 1920x1080 | 13.9 | 2018 | [6CEB8E4522B9](<Digital/AU Optronics/AUO563D/6CEB8E4522B9>) |
| AU Optronics     | AUO5699 |                  | 1920x1080 | 15.3 | 2021 | [458A40EAFF1E](<Digital/AU Optronics/AUO5699/458A40EAFF1E>) |
| AU Optronics     | AUO56AD |                  | 1920x1080 | 17.3 | 2023 | [6FB2B208AA74](<Digital/AU Optronics/AUO56AD/6FB2B208AA74>) |
| AU Optronics     | AUO56D4 | B101EW05 V6      | 1280x800  | 10.3 | 2010 | [6523E27613F0](<Digital/AU Optronics/AUO56D4/6523E27613F0>) |
| AU Optronics     | AUO572D |                  | 1920x1080 | 13.2 | 2018 | [5252F5CCEA61](<Digital/AU Optronics/AUO572D/5252F5CCEA61>) |
| AU Optronics     | AUO573D | B140HAN05.7      | 1920x1080 | 13.9 | 2021 | [17E92962DAF4](<Digital/AU Optronics/AUO573D/17E92962DAF4>) |
| AU Optronics     | AUO573D | B140HAN05.7      | 1920x1080 | 13.9 | 2018 | [5627D8FDEB54](<Digital/AU Optronics/AUO573D/5627D8FDEB54>) |
| AU Optronics     | AUO5793 | NXPHX            | 1920x1080 | 17.3 | 2021 | [C219655A7BC4](<Digital/AU Optronics/AUO5793/C219655A7BC4>) |
| AU Optronics     | AUO5799 |                  | 1920x1080 | 15.3 | 2021 | [3B0C8499B35F](<Digital/AU Optronics/AUO5799/3B0C8499B35F>) |
| AU Optronics     | AUO582D | B133HAN05.8      | 1920x1080 | 13.2 | 2018 | [3DB77F6A37E2](<Digital/AU Optronics/AUO582D/3DB77F6A37E2>) |
| AU Optronics     | AUO583D | B140HAN05.8      | 1920x1080 | 13.9 | 2018 | [5C086FB54566](<Digital/AU Optronics/AUO583D/5C086FB54566>) |
| AU Optronics     | AUO5890 |                  | 1366x768  | 15.3 | 2020 | [F22253BF463E](<Digital/AU Optronics/AUO5890/F22253BF463E>) |
| AU Optronics     | AUO5895 | B156HAN12.H      | 1920x1080 | 15.3 | 2020 | [178E836336F5](<Digital/AU Optronics/AUO5895/178E836336F5>) |
| AU Optronics     | AUO592D | B133HAN05.9      | 1920x1080 | 13.2 | 2018 | [6D79938A6329](<Digital/AU Optronics/AUO592D/6D79938A6329>) |
| AU Optronics     | AUO593D |                  | 1920x1080 | 13.9 | 2018 | [83F7B549B8DE](<Digital/AU Optronics/AUO593D/83F7B549B8DE>) |
| AU Optronics     | AUO598F | B156HAN13.2      | 1920x1080 | 15.3 | 2019 | [703ADB4820CC](<Digital/AU Optronics/AUO598F/703ADB4820CC>) |
| AU Optronics     | AUO5A2D | B133HAN05.A      | 1920x1080 | 13.2 | 2018 | [223B5E3EAFF0](<Digital/AU Optronics/AUO5A2D/223B5E3EAFF0>) |
| AU Optronics     | AUO5A3D | B140HAN05.A      | 1920x1080 | 13.9 | 2018 | [B41D2AAD3CCE](<Digital/AU Optronics/AUO5A3D/B41D2AAD3CCE>) |
| AU Optronics     | AUO5A41 | J5596            | 1024x768  | 14.1 |      | [53FF60C432DF](<Digital/AU Optronics/AUO5A41/53FF60C432DF>) |
| AU Optronics     | AUO5A99 |                  | 1920x1200 | 14.0 | 2021 | [750139559722](<Digital/AU Optronics/AUO5A99/750139559722>) |
| AU Optronics     | AUO5AB1 | 42F9F            | 2560x1600 | 15.9 | 2024 | [E60C7ECC3F5C](<Digital/AU Optronics/AUO5AB1/E60C7ECC3F5C>) |
| AU Optronics     | AUO5B2D | 06VG6            | 1920x1080 | 13.0 | 2018 | [142FD7252EF0](<Digital/AU Optronics/AUO5B2D/142FD7252EF0>) |
| AU Optronics     | AUO5B94 | HTYXJ            | 1366x768  | 15.3 | 2019 | [82FD1BE330AA](<Digital/AU Optronics/AUO5B94/82FD1BE330AA>) |
| AU Optronics     | AUO5C2D | B133HAN05.C      | 1920x1080 | 13.2 | 2018 | [A4368CDBDCF9](<Digital/AU Optronics/AUO5C2D/A4368CDBDCF9>) |
| AU Optronics     | AUO5C9C | WF0NX            | 1920x1080 | 15.3 | 2021 | [9A97E79A36A6](<Digital/AU Optronics/AUO5C9C/9A97E79A36A6>) |
| AU Optronics     | AUO5D2D |                  | 1920x1080 | 13.2 | 2018 | [9A67ED8F5A84](<Digital/AU Optronics/AUO5D2D/9A67ED8F5A84>) |
| AU Optronics     | AUO5DA7 | B140QAN06.U      | 2560x1600 | 14.0 | 2022 | [34E4F2227EAF](<Digital/AU Optronics/AUO5DA7/34E4F2227EAF>) |
| AU Optronics     | AUO5E2D |                  | 1920x1080 | 13.2 | 2018 | [91D5C26D90A1](<Digital/AU Optronics/AUO5E2D/91D5C26D90A1>) |
| AU Optronics     | AUO5EAD |                  | 1920x1200 | 15.9 | 2023 | [EA25F9284BC3](<Digital/AU Optronics/AUO5EAD/EA25F9284BC3>) |
| AU Optronics     | AUO5EB2 | 8R4CX            | 1920x1200 | 15.9 | 2024 | [8334EB55C476](<Digital/AU Optronics/AUO5EB2/8334EB55C476>) |
| AU Optronics     | AUO5F2D | B133HAN05.F      | 1920x1080 | 13.2 | 2019 | [163690745A07](<Digital/AU Optronics/AUO5F2D/163690745A07>) |
| AU Optronics     | AUO5F2D | B133HAN05.H      | 1920x1080 | 13.2 | 2018 | [A53602FC47EA](<Digital/AU Optronics/AUO5F2D/A53602FC47EA>) |
| AU Optronics     | AUO6024 | B133EW06 V0      | 1280x800  | 13.4 | 2008 | [26E02E667220](<Digital/AU Optronics/AUO6024/26E02E667220>) |
| AU Optronics     | AUO602D | 52F4N            | 1920x1080 | 13.2 | 2017 | [F1D849408D06](<Digital/AU Optronics/AUO602D/F1D849408D06>) |
| AU Optronics     | AUO603D | B140HAN06.0      | 1920x1080 | 13.9 | 2018 | [39942D120AE9](<Digital/AU Optronics/AUO603D/39942D120AE9>) |
| AU Optronics     | AUO607A | 7115H            | 1366x768  | 15.3 | 2019 | [29DE33E76487](<Digital/AU Optronics/AUO607A/29DE33E76487>) |
| AU Optronics     | AUO6092 | C9PFN            | 1920x1080 | 15.3 | 2020 | [B6E7FC6E34FD](<Digital/AU Optronics/AUO6092/B6E7FC6E34FD>) |
| AU Optronics     | AUO60A3 |                  | 3072x1920 | 15.9 | 2021 | [BDA369EB4305](<Digital/AU Optronics/AUO60A3/BDA369EB4305>) |
| AU Optronics     | AUO60D2 | B101AW06 V0      | 1024x600  | 10.1 | 2009 | [48256152E47A](<Digital/AU Optronics/AUO60D2/48256152E47A>) |
| AU Optronics     | AUO60ED | Y502X            | 1920x1080 | 15.3 | 2016 | [12822444C57A](<Digital/AU Optronics/AUO60ED/12822444C57A>) |
| AU Optronics     | AUO60ED | Y502X            | 1920x1080 | 15.3 |      | [7F34A70486C1](<Digital/AU Optronics/AUO60ED/7F34A70486C1>) |
| AU Optronics     | AUO612D | B133HAN06.1      | 1920x1080 | 13.2 | 2017 | [B6B96CA7836A](<Digital/AU Optronics/AUO612D/B6B96CA7836A>) |
| AU Optronics     | AUO613D |                  | 1920x1080 | 13.9 | 2018 | [23729FC1440C](<Digital/AU Optronics/AUO613D/23729FC1440C>) |
| AU Optronics     | AUO615C |                  | 1366x768  | 11.6 | 2018 | [996DBBC2E25F](<Digital/AU Optronics/AUO615C/996DBBC2E25F>) |
| AU Optronics     | AUO615C |                  | 1366x768  | 11.6 | 2017 | [63461405D5AA](<Digital/AU Optronics/AUO615C/63461405D5AA>) |
| AU Optronics     | AUO61D2 | B101AW06 V1      | 1024x600  | 10.1 | 2009 | [84528A4C299B](<Digital/AU Optronics/AUO61D2/84528A4C299B>) |
| AU Optronics     | AUO61ED |                  | 1920x1080 | 15.3 | 2023 | [6543DB27811F](<Digital/AU Optronics/AUO61ED/6543DB27811F>) |
| AU Optronics     | AUO61ED |                  | 1920x1080 | 15.3 | 2021 | [0561E683BC79](<Digital/AU Optronics/AUO61ED/0561E683BC79>) |
| AU Optronics     | AUO61ED |                  | 1920x1080 | 15.3 | 2018 | [257CDE938AD2](<Digital/AU Optronics/AUO61ED/257CDE938AD2>) |
| AU Optronics     | AUO61ED | B156HAN06.1      | 1920x1080 | 15.3 | 2016 | [6AF3279E7F45](<Digital/AU Optronics/AUO61ED/6AF3279E7F45>) |
| AU Optronics     | AUO622D | NTRKG            | 1920x1080 | 13.2 | 2018 | [6088C7126867](<Digital/AU Optronics/AUO622D/6088C7126867>) |
| AU Optronics     | AUO623D | B140HAN06.2      | 1920x1080 | 13.9 | 2019 | [B685B52742CA](<Digital/AU Optronics/AUO623D/B685B52742CA>) |
| AU Optronics     | AUO623D | B140HAN06.2      | 1920x1080 | 13.9 | 2018 | [0EA00EE81D2B](<Digital/AU Optronics/AUO623D/0EA00EE81D2B>) |
| AU Optronics     | AUO6287 | WU342            | 1440x900  | 17.2 | 2007 | [1CC61ABF0F01](<Digital/AU Optronics/AUO6287/1CC61ABF0F01>) |
| AU Optronics     | AUO632D | F64N5            | 1920x1080 | 13.2 | 2018 | [7F2EC2D7A0AD](<Digital/AU Optronics/AUO632D/7F2EC2D7A0AD>) |
| AU Optronics     | AUO633D | MJXRM            | 1920x1080 | 13.9 | 2019 | [62FF72AC6036](<Digital/AU Optronics/AUO633D/62FF72AC6036>) |
| AU Optronics     | AUO635C |                  | 1366x768  | 11.6 | 2017 | [225F5547452B](<Digital/AU Optronics/AUO635C/225F5547452B>) |
| AU Optronics     | AUO6387 | T990J            | 1440x900  | 17.2 | 2009 | [48508FED0620](<Digital/AU Optronics/AUO6387/48508FED0620>) |
| AU Optronics     | AUO6387 | RM221            | 1440x900  | 17.2 | 2008 | [AE2945E90A59](<Digital/AU Optronics/AUO6387/AE2945E90A59>) |
| AU Optronics     | AUO6387 | U580C /BP[       | 1440x900  | 17.2 | 2007 | [8207C2130740](<Digital/AU Optronics/AUO6387/8207C2130740>) |
| AU Optronics     | AUO639C |                  | 1920x1080 | 13.9 | 2021 | [27DCB5851AE5](<Digital/AU Optronics/AUO639C/27DCB5851AE5>) |
| AU Optronics     | AUO63ED |                  | 1920x1080 | 15.3 | 2018 | [7CC023E7525F](<Digital/AU Optronics/AUO63ED/7CC023E7525F>) |

...

See full list of digital monitors in the [DigitalDisplay.md](<DigitalDisplay.md>) file.

Analog display
--------------

See list of analog monitors in the [AnalogDisplay.md](<AnalogDisplay.md>) file.

