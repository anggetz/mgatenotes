# Function

## Substr
untuk mengambil charset dari bit atau field:

support processor: DataSetter.so
```
<set bit="102">
    <data bit="102">
      <func name="substr"><substr from="3"/></func>
    </data>
</set>
```

## len str
menghitung panjang length dari karakter

support processor: DataSetter.so
```
<func name="str">len</func>
```

## Calc
melakukan kalkulasi
$val = field yang sedang dikalkulasi

support processor: DataSetter.so
```
<set bit="4">
    <data bit="4">
        <func name="calc">$val x 100</func>
    </data>
</set>
```

## Map
melakukan map value yang akan diubah di second value

support processor: DataSetter.so
```
<set bit="70">
    <data bit="70">
        <func name="map">
            001=061 | 101=301 | 002=062 | 142=101 | 141=101
        </func>
    </data>
</set>
```

maksud diatas bit70 dengan value 001 akan diubah menjadi 061 dst.

## Datefmt
format date

support processor: DataSetter.so
```
<func name="datefmt">0102150405 | 0102</func>
```

## Decfmt
format decimal

support processor: DataSetter.so
```
<func name="decfmt">0 | %012.f</func>
```

## hash
hashing karakter

support processor: DataSetter.so
```
<set field="hex39">
    <data bit="39">
        <func name="hash">none | hex</func>
    </data>
</set>
```

## timecalc
kakulasi waktu

support processor: DataSetter.so
```
<func name="timecalc">0102 | +1d</func>
```

## timezone
set timezone value waktu

support processor: DataSetter.so
```
<set bit="7">
    <data bit="7">
        <func name="timezone">0102150405 | Asia/Manila | GMT</func>
    </data>
</set>
```

## replace
mengganti karakter old ke karakter new

support processor: DataSetter.so
```
<func name="replace">
    <replace old="U" new="" />
</func>
```
