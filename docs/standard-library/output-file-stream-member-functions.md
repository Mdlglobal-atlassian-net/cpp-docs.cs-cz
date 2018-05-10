---
title: Výstup členské funkce datového proudu souboru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1cba80b18f94d5a833b238e19be8190a442146
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="output-file-stream-member-functions"></a>Členské funkce datového proudu výstupního souboru

Členské funkce datového proudu výstupního mít tři typy: ty, které odpovídají manipulátory, takové, které provádějí neformátovaný operací zápisu, a ty, které jinak změnit datový proud stavu a mít žádná ekvivalentní manipulator nebo operátor vložení. Pro sekvenční, formátovaný výstup můžete použít pouze operátorů insertion a manipulátory. Pro výstup disku binární náhodný přístup použijte jiné členské funkce s nebo bez operátorů insertion.

## <a name="the-open-function-for-output-streams"></a>Otevřete funkce pro výstupní datové proudy

Použít soubor výstupního datového proudu ([ofstream](../standard-library/basic-ofstream-class.md)), je třeba přidružit tohoto datového proudu k souboru na konkrétní disku v konstruktoru nebo **otevřete** funkce. Pokud použijete **otevřete** funkce, můžete znovu použít stejný objekt datového proudu s řadou soubory. V obou případech jsou argumenty popisující soubor stejné.

Když otevřete soubor přidružený výstupního datového proudu, obvykle určují **open_mode** příznak. Zkombinováním tyto příznaky, které jsou definovány jako výčty v `ios` třídě, bitová hodnota OR ( &#124; ) operátor. V tématu [ios_base::openmode](../standard-library/ios-base-class.md#openmode) seznam výčty.

Tři běžné situace výstupní datový proud zahrnovat možnosti režimu:

- Vytvoření souboru. Pokud soubor již existuje, je odstranit staré verze.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Přidávání záznamů existující soubor nebo vytvořit Pokud neexistuje.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Otevírání dva soubory, jeden po druhém, do stejného datového proudu.

   ```cpp
   ofstream ofile();
   ofile.open("FILE1", ios::in);
   // Do some output
   ofile.close();    // FILE1 closed
   ofile.open("FILE2", ios::in);
   // Do some more output
   ofile.close();    // FILE2 closed
   // When ofile goes out of scope it is destroyed.
   ```

## <a name="the-put"></a>Put

**Put** funkce zapíše do výstupního datového proudu jeden znak. Následující dva příkazy jsou stejné ve výchozím nastavení, ale druhý je ovlivňován datový proud formátu argumenty:

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>Zápis

**Zápisu** funkce zapíše do výstupního datového proudu souboru bloku paměti. Délka argumentu určuje počet zapsaných bajtů. Tento příklad vytvoří výstupní datový proud souboru a zapíše binární hodnotu `Date` k jeho strukturu:

```cpp
// write_function.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;

struct Date
{
   int mo, da, yr;
};

int main( )
{
   Date dt = { 6, 10, 92 };
   ofstream tfile( "date.dat" , ios::binary );
   tfile.write( (char *) &dt, sizeof dt );
}
```

**Zápisu** funkce nezastaví při dosažení prázdný znak, tak se zapíše struktura dokončení třídy. Funkce má dva argumenty: `char` ukazatel a počet znaků k zápisu. Všimněte si požadované přetypování na **char\***  před adresu struktura objektu.

## <a name="the-seekp-and-tellp-functions"></a>Seekp – a tellp – funkce

Výstupní datový proud souboru udržuje interní ukazatele, který odkazuje na pozici, kde je dat k zapsání Další. `seekp` – Členská funkce nastaví tento ukazatel a tak poskytuje náhodný přístup disku výstupního souboru. `tellp` – Členská funkce vrátí pozice v souboru. Příklady, které používají ekvivalenty vstupního datového proudu k `seekp` a `tellp`, najdete v části [funkce seekg – a tellg –](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>Zavřít funkce pro výstupní datové proudy

**Zavřete** – členská funkce zavře soubor disku přidružené výstupní datový proud souboru. Soubor musí být uzavřena do dokončení veškerý výstup disku. V případě potřeby `ofstream` destruktor zavře soubor pro vás, ale můžete použít **zavřete** fungovat, pokud je třeba otevřít jiný soubor pro stejný objekt datového proudu.

Výstupní datový proud destruktoru automaticky zavře datový proud souboru pouze v případě konstruktoru nebo **otevřete** – členská funkce Otevřít soubor. Pokud předáte konstruktoru popisovač souboru pro soubor už otevřený, nebo použijte **připojit** – členská funkce, je třeba nejprve zavřít soubor explicitně.

## <a name="vclrferrorprocessingfunctionsanchor10"></a> Chyba zpracování funkce

Pomocí těchto členských funkcí testování chyb při zápisu do datového proudu:

|Funkce|Návratová hodnota|
|--------------|------------------|
|[Špatné](http://msdn.microsoft.com/Library/4038d331-e9c9-48b0-bf49-c6505744469c)|Vrátí **true** Pokud dojde k neodstranitelné chybě.|
|[Selhání](http://msdn.microsoft.com/Library/619f1b36-1e72-4551-8b48-888ae4e370d2)|Vrátí **true** Pokud dojde k neodstranitelné chybě nebo podmínku "očekávané", jako je Chyba převodu, nebo pokud soubor nebyl nalezen. Zpracování můžete často obnovit po volání **vymazat** s argumentem nula.|
|[Dobré](http://msdn.microsoft.com/Library/77f0aa17-2ae1-48ae-8040-592d301e3972)|Vrátí **true** Pokud není žádná chybová podmínka (neopravitelné nebo jinak) a není nastaven příznak end souboru.|
|[eof](http://msdn.microsoft.com/Library/3087f631-1268-49cd-86cf-ff4108862329)|Vrátí **true** na podmínky end souboru.|
|[Zrušte zaškrtnutí](http://msdn.microsoft.com/Library/dc172694-1267-45f8-8f5c-e822e16fc271)|Nastaví stav vnitřní chybě. Pokud je volána s výchozí argumenty, vymaže všechny chyby služby bits.|
|[rdstate –](http://msdn.microsoft.com/Library/e235e4e2-7e95-4777-a160-3938d263dd9c)|Vrátí aktuální chybový stav.|

**!** operátor je přetížena provést totéž, jako **nezdaří** funkce. Proto výraz:

```cpp
if(!cout)...
```

je ekvivalentní:

```cpp
if(cout.fail())...
```

**Void\*()** operátor je přetížena být opakem **!** operátor; proto výraz:

```cpp
if(cout)...
```

se rovná:

```cpp
if(!cout.fail())...
```

**Void\*()** operátor není ekvivalentní **dobrý** vzhledem k tomu, že není testování pro konec souboru.

## <a name="see-also"></a>Viz také

[Výstupní streamy](../standard-library/output-streams.md)<br/>
