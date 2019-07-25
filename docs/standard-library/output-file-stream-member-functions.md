---
title: Členské funkce datového proudu výstupního souboru
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: 8c23008d0c46a532f11e89442328ed25cc203077
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453055"
---
# <a name="output-file-stream-member-functions"></a>Členské funkce datového proudu výstupního souboru

Členské funkce výstupního datového proudu mají tři typy: ty, které jsou ekvivalentní manipulacím, ty, které provádějí neformátované operace zápisu, a ty, které jinak mění stav datového proudu a nemají ekvivalentní manipulátor nebo operátor vložení. U sekvenčních, formátovaných výstupů můžete použít jenom operátory vložení a manipuluje. Pro výstup binárního disku s náhodným přístupem můžete použít jiné členské funkce s operátory vložení nebo bez nich.

## <a name="the-open-function-for-output-streams"></a>Funkce Open pro výstupní datové proudy

Chcete-li použít výstupní soubor Stream ([ofstream](../standard-library/basic-ofstream-class.md)), je nutné tento datový proud přidružit k určitému souboru na disku v `open` konstruktoru nebo funkci. Použijete-li `open` funkci, můžete použít stejný objekt datového proudu s řadou souborů. V obou případech jsou argumenty popisující soubor stejné.

Když otevřete soubor přidružený k výstupnímu datovému proudu, obecně určíte `open_mode` příznak. Tyto příznaky, které jsou definovány jako enumerátory ve `ios` třídě, lze kombinovat pomocí operátoru bitového operátoru OR ( &#124; ). Seznam enumerátorů naleznete v tématu [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) .

Mezi tři běžné situace výstupního streamu patří možnosti režimu:

- Vytváření souboru. Pokud soubor už existuje, stará verze se odstraní.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Připojení záznamů k existujícímu souboru nebo vytvoření jednoho, pokud neexistuje.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Otevírání dvou souborů současně ve stejném datovém proudu.

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

## <a name="the-put"></a>Vložení

Funkce **Put** zapisuje jeden znak do výstupního datového proudu. Následující dva příkazy jsou ve výchozím nastavení stejné, ale druhá má vliv na argumenty formátu datového proudu:

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>Zápis

`write` Funkce zapisuje do datového proudu výstupního souboru blok paměti. Argument Length určuje počet zapsaných bajtů. Tento příklad vytvoří datový proud výstupního souboru a zapíše do něj binární `Date` hodnotu struktury:

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

`write` Funkce se nezastaví, když dosáhne znaku null, takže je zapsána kompletní struktura třídy. Funkce přebírá dva argumenty: ukazatel typu **char** a počet znaků, které mají být zapsány. Všimněte si, že požadované přetypování na typ **char** <strong>\*</strong> před adresou objektu struktury.

## <a name="the-seekp-and-tellp-functions"></a>Funkce seekp a tellp

Stream výstupního souboru udržuje vnitřní ukazatel, který odkazuje na pozici, kde se mají data zapsat. `seekp` Členská funkce nastaví tento ukazatel, takže poskytuje výstup souboru disku s náhodným přístupem. `tellp` Členská funkce vrátí pozici souboru. Příklady, které používají ekvivalent `seekp` vstupního datového proudu v a `tellp`, naleznete v tématu [funkce seekg a tellg](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>Funkce Close pro výstupní datové proudy

`close` Členská funkce zavře soubor disku přidružený ke streamu výstupního souboru. Aby bylo možné dokončit všechny výstupy na disku, je třeba zavřít soubor. V případě potřeby `ofstream` destruktor soubor zavře za vás, ale `close` funkci můžete použít, pokud potřebujete otevřít jiný soubor pro stejný objekt streamu.

Destruktor výstupního datového proudu automaticky zavře soubor datového proudu pouze v případě, že konstruktor `open` nebo členská funkce otevřela soubor. Pokud předáte konstruktoru popisovač souboru pro již otevřený soubor nebo použijete `attach` členskou funkci, musíte soubor explicitně zavřít.

## <a name="vclrferrorprocessingfunctionsanchor10"></a>Chyba při zpracování funkcí

Pomocí těchto členských funkcí otestujete chyby při zápisu do datového proudu:

|Funkce|Návratová hodnota|
|--------------|------------------|
|[Špatné](basic-ios-class.md#bad)|Vrátí **hodnotu true** , pokud dojde k neopravitelné chybě.|
|[proběhne](basic-ios-class.md#fail)|Vrátí **hodnotu true** , pokud existuje Neopravitelná chyba nebo podmínka "Očekávaná", například Chyba převodu, nebo pokud soubor nebyl nalezen. Zpracování může často pokračovat po volání `clear` s nulovým argumentem.|
|[Dobré](basic-ios-class.md#good)|Vrátí **hodnotu true** , pokud neexistuje chybový stav (neobnovitelné nebo jinak) a příznak konce souboru není nastaven.|
|[eof](basic-ios-class.md#eof)|Vrátí **hodnotu true** pro podmínku konce souboru.|
|[jejich](basic-ios-class.md#clear)|Nastaví stav interní chyby. Pokud se volá s výchozími argumenty, vymaže všechny chybové bity.|
|[rdstate] (Basic-iOS-Class. MD # rdstate|Vrátí aktuální chybový stav.|

**.** operátor je přetížen, aby prováděl stejnou funkci jako `fail` funkce. Výraz tedy:

```cpp
if(!cout)...
```

je ekvivalentní:

```cpp
if(cout.fail())...
```

Operátor **void\*()** je přetížený tak, aby byl opakem **!** podnikatel výraz tedy:

```cpp
if(cout)...
```

je rovno:

```cpp
if(!cout.fail())...
```

Operátor **void\*()** není ekvivalentní k `good` tomu, protože netestuje na konci souboru.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)
