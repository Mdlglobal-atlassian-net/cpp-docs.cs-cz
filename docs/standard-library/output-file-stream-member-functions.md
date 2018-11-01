---
title: Členské funkce datového proudu výstupního souboru
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: eba627c69437754a9c0a819167443aa00c025fef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621764"
---
# <a name="output-file-stream-member-functions"></a>Členské funkce datového proudu výstupního souboru

Výstupní datový proud členské funkce mají tři typy: ty, které jsou ekvivalentní manipulátory, ty, které provádějí neformátovaný operace zápisu, a ty, které jinak upravit datový proud stavu a mít žádná ekvivalentní manipulátor nebo operátor vkládání. Pro sekvenční, formátovaný výstup můžete použít pouze operátorů insertion a manipulátory. Pro výstup disku binární náhodný přístup použijte jiné členské funkce, s nebo bez něj operátorů insertion.

## <a name="the-open-function-for-output-streams"></a>Funkce open pro výstupní datové proudy

Použití výstupní datový proud souboru ([ofstream](../standard-library/basic-ofstream-class.md)), musíte přidružit k tohoto datového proudu souboru na konkrétní disku v konstruktoru nebo `open` funkce. Pokud používáte `open` funkce, můžete znovu použít stejný objekt stream s řadou soubory. V obou případech jsou argumenty popisující soubor stejné.

Když otevřete soubor přidružený k výstupní datový proud, obvykle určují `open_mode` příznak. Můžete kombinovat tyto příznaky, které jsou definovány jako výčty v `ios` třídy s bitový operátor OR ( &#124; ) – operátor. Zobrazit [ios_base::openmode](../standard-library/ios-base-class.md#openmode) seznam čítačů.

Tři běžné situace výstupní datový proud zahrnují možnosti režimu:

- Vytvoření souboru. Pokud soubor již existuje, se odstraní staré verze.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Přidání záznamů do existujícího souboru nebo vytvoření nového, pokud neexistuje.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Otevírá dva soubory, jeden po druhém, stejný datový proud.

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

**Umístit** funkce zapíše jeden znak do výstupního datového proudu. Následující dva příkazy jsou stejné ve výchozím nastavení, ale druhá je ovlivněna argumentů formátu datového proudu:

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>Zápis

`write` Funkce zapíše do výstupního datového proudu souboru blok paměti. Argument délky určuje počet zapsaných bajtů. Tento příklad vytvoří výstupní datový proud souboru a zapíše binární hodnotu `Date` strukturu do ní:

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

`write` Funkce nezastaví ji po dosažení prázdný znak, takže zapisován struktura úplné třídy. Funkce přebírá dva argumenty: **char** ukazatele a počet znaků k zápisu. Poznámka: vyžaduje přetypování na **char** <strong>\*</strong> než adresu objektu struktury.

## <a name="the-seekp-and-tellp-functions"></a>Seekp – a tellp – funkce

Výstupní datový proud souboru udržuje interní ukazatel, který odkazuje na umístění, ve kterém jsou data k zapsání dále. `seekp` Členská funkce nastaví tento ukazatel a tak poskytuje náhodný přístup disku výstupního souboru. `tellp` Členská funkce vrátí pozice v souboru. Příklady, které používají ekvivalenty vstupního datového proudu k `seekp` a `tellp`, naleznete v tématu [funkce seekg – a tellg –](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>Zavřít funkce pro výstupní datové proudy

`close` Členská funkce se zavře souboru na disku, který je přidružený k výstupní datový proud souboru. Soubor musí být uzavřena do dokončení veškerý výstup disku. V případě potřeby `ofstream` destruktor zavře soubor, který pro vás, ale můžete použít `close` fungovat, pokud je potřeba otevřít další soubor pro stejný objekt datového proudu.

Výstupní datový proud destruktor automaticky zavře datový proud souboru pouze tehdy, pokud konstruktor nebo `open` členská funkce Otevřít soubor. Pokud předáte konstruktoru popisovač souboru pro soubor již otevřít nebo použít `attach` členskou funkci, musíte zavřít soubor explicitně.

## <a name="vclrferrorprocessingfunctionsanchor10"></a> Funkce zpracování chyb

K testování chyby při zápisu do datového proudu použijte tyto členské funkce:

|Funkce|Návratová hodnota|
|--------------|------------------|
|[Špatné](basic-ios-class.md#bad)|Vrátí **true** Pokud dojde k neodstranitelné chybě.|
|[Selhání](basic-ios-class.md#fail)|Vrátí **true** dojde k neodstranitelné chybě nebo "očekávané" podmínku, třeba Chyba převodu, nebo pokud se nenajde soubor. Zpracování může často pokračovat po volání `clear` s argumentem nula.|
|[Dobré](basic-ios-class.md#good)|Vrátí **true** Pokud neexistuje žádná chybová podmínka (neobnovitelná nebo jinak) a není nastaven příznak end souboru.|
|[eof](basic-ios-class.md#eof)|Vrátí **true** ve stavu ukončení souboru.|
|[Vymazat](basic-ios-class.md#clear)|Nastaví stav vnitřní chyba. Pokud je volána pomocí výchozích argumentů, vymaže všechny bity chyby.|
|[rdstate –] (basic-ios-class.md #rdstate|Vrátí aktuální chybový stav.|

**!** k provedení stejné funkce jako je operátor přetížen `fail` funkce. Proto výraz:

```cpp
if(!cout)...
```

je ekvivalentní:

```cpp
if(cout.fail())...
```

**Void\*()** je operátor přetížen, chcete-li být opakem toho, **!** operátor; proto výraz:

```cpp
if(cout)...
```

je rovno:

```cpp
if(!cout.fail())...
```

**Void\*()** operátor není ekvivalentní `good` protože netestuje konec souboru.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
