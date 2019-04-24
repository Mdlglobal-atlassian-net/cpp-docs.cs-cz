---
title: x64 softwarové konvence
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313825"
---
# <a name="x64-software-conventions"></a>x64 softwarové konvence

Tato část popisuje metodologii konvence volání pro x64 rozšíření 64-bit x86 C++ architektury.

## <a name="overview-of-x64-calling-conventions"></a>Přehled x64 konvence volání

Jsou dva důležité rozdíly mezi x86 a x64 schopnosti adresování 64bitovým kompilátorem a ploché sady 16 64-bit zaregistruje pro obecné použití. Zadané sady rozšířené registr, používá x64 [__fastcall](../cpp/fastcall.md) volání vytváření názvů a jako model založený na RISC zpracování výjimek. `__fastcall` Konvence používá registry pro prvních čtyř argumentů a rámce zásobníku pro předání dalších argumentů. Pro parametry zásobníku podrobnosti o x64 konvence volání, včetně využití registrů, vrátit hodnoty a uvolnění zásobníku, naleznete v tématu [x64 konvence volání](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Povolit optimalizace pro x64

Následující možnost kompilátoru umožňuje optimalizovat aplikaci pro x64:

- [/favor (optimalizace pro konkrétní architekturu)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Typy a úložiště

Tato část popisuje, výčet a ukládání datových typů pro x64 architektury.

### <a name="scalar-types"></a>Skalární typy

I když je možné získat přístup k datům pomocí jakékoli zarovnání, doporučuje se zarovnání dat na jejich přirozené hranice nebo některé více, aby nedošlo ke ztrátě výkonu. Výčty jsou konstantních celých čísel a jsou považovány za 32bitová celá čísla. Následující tabulka popisuje definice typu a doporučené úložiště pro data, protože se týkají zarovnání použitím následujících hodnot zarovnání:

- Byte – 8 bitů

- Word – 16 bitů

- Doubleword - 32 bitů

- Quadword - 64 bitů

- Octaword - 128 bitů

|||||
|-|-|-|-|
|Skalární typ.|Datový typ jazyka C|Velikost úložiště (v bajtech)|Doporučené zarovnání|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**short bez znaménka**|2|Word|
|**INT32**|**int**, **dlouhý**|4|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|4|Doubleword|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**unsigned __int64**|8|Quadword|
|**FP32 (jednoduché přesnosti)**|**float**|4|Doubleword|
|**FP64 (Dvojitá přesnost)**|**double**|8|Quadword|
|**UKAZATEL**|__\*__|8|Quadword|
|**__m64**|**__m64 – struktura**|8|Quadword|
|**__m128**|**struct __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agregace a sjednocení

Jiné typy, jako je například pole, struktury a sjednocení, mít přísnější požadavky na zarovnání, které zajišťují konzistentní agregace a sjednocení načítání úložiště a data. Zde najdete definice pro pole, struktury a sjednocení:

- Pole

   Obsahuje skupinu seřazený sousedními datovými objekty. Každý objekt je volána *element*. Všechny prvky v rámci pole mají stejnou velikost a datový typ.

- Struktura

   Obsahuje skupinu seřazený datových objektů. Na rozdíl od prvků pole datových objektů v rámci struktury můžete mít různé datové typy a velikosti. Každý datový objekt ve struktuře je volána *člen*.

- Unie

   Objekt, který obsahuje některý ze sady pojmenované členy. Členové pojmenovaná sada může být libovolného typu. Úložiště přidělené pro sjednocení je rovna požadované pro největšího člena v tomto sjednocení, plus všechny odsazení na zarovnání.

V následující tabulce jsou uvedeny důrazně doporučené zarovnání skalární členy struktury a sjednocení.

||||
|-|-|-|
|Skalární typ.|Datový typ jazyka C|Požadované zarovnání|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**short bez znaménka**|Word|
|**INT32**|**int**, **dlouhý**|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|Doubleword|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 (jednoduché přesnosti)**|**float**|Doubleword|
|**FP64 (Dvojitá přesnost)**|**double**|Quadword|
|**UKAZATEL**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 – struktura**|Quadword|
|**__m128**|**struct __m128**|Octaword|

Platí následující pravidla agregační zarovnání:

- Zarovnání pole je stejná jako zarovnání prvků pole.

- Zarovnání začátek struktury nebo sjednocení je maximální zarovnání každého jednotlivého člena. Každý člen v rámci struktury nebo sjednocení musí být umístěny na správném zarovnání, jak je definováno v předchozí tabulce, která může vyžadovat implicitní vnitřní odsazení, v závislosti na předchozí člen.

- Velikost struktury musí být integrální násobek jeho zarovnání, které mohou vyžadovat odsazení za posledním členem. Protože struktury a sjednocení mohou být seskupeny do pole, musí každý prvek pole, struktury nebo sjednocení začínají i končí na řádné zarovnání dříve určené.

- Je možné zarovnání dat tak, aby byly větší než požadavky na zarovnání jako předchozí pravidla jsou zachována.

- Jednotlivé kompilátor může upravit balení struktury důvodů velikost. Například [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md) umožňuje pro úpravu balení struktury.

### <a name="examples-of-structure-alignment"></a>Příklady zarovnání struktur

Následující čtyři příklady každou deklaraci že zarovnané struktury nebo sjednocení a odpovídající obrázky znázorňují rozložení této struktury nebo sjednocení v paměti. Každý sloupec v elementu figure reprezentuje bajt paměti a číslo ve sloupci určuje posunutí daného bajtu. Název ve druhém řádku každý obrázek odpovídá názvu proměnné v prohlášení. Sloupců indikoval odsazení, která je potřebná k dosažení zadané zarovnání.

#### <a name="example-1"></a>Příklad 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Rozložení struktury – Příklad 1 převod AMD](../build/media/vcamd_conv_ex_1_block.png "AMD převod – Příklad 1 struktuře rozložení")

#### <a name="example-2"></a>Příklad 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Rozložení struktury příklad 2 převod AMD](../build/media/vcamd_conv_ex_2_block.png "AMD převod příklad 2 struktuře rozložení")

#### <a name="example-3"></a>Příklad 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Rozložení struktury příklad 2 převod AMD](../build/media/vcamd_conv_ex_3_block.png "AMD převod příklad 2 struktuře rozložení")

#### <a name="example-4"></a>Příklad 4:

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Sjednocení layouit příklad 4: AMD převod](../build/media/vcamd_conv_ex_4_block.png "sjednocení layouit AMD převod příklad 4:")

### <a name="bitfields"></a>Bitová pole

Struktura bitová pole jsou omezené na 64 bitů a nemůže být typu int, unsigned int, int64 nebo bez znaménka int64 podepsané. Bitová pole, které překračují hranice typu přeskočí bits zarovnáním zarovnání dalšího typu. Například bitová pole celé číslo nemusí napříč autonomního 32-bit.

### <a name="conflicts-with-the-x86-compiler"></a>Je v konfliktu s x86 kompilátoru

Datové typy, které jsou větší než 4 bajty nejsou zarovnány automaticky v zásobníku při použití x86 kompilátoru kompilovat aplikace. Protože architektura x86 kompilátoru je 4 bajty. zarovnané zásobníku, nic větší než 4 bajty, například 64bitové celé číslo, nelze automaticky zarovnány na adresu 8 bajtů.

Práce s nezarovnaná data po má dva důsledky.

- Může trvat déle, získat přístup k umístění nezarovnaných trvá pro přístup k umístěním zarovnaný.

- Nezarovnané umístění nelze použít v propojené operace.

Pokud budete potřebovat více striktní zarovnání, použijte `__declspec(align(N))` v deklaracích proměnných. To způsobí, že kompilátor, aby dynamicky zarovnat stack pro splnění vašich požadavků. Dynamické úpravy do zásobníku za běhu však může způsobit pomalejší spuštění vaší aplikace.

## <a name="register-usage"></a>Využití registrů

X64, které poskytuje architekturu pro 16 pro obecné účely registrů (dále jako celočíselné registry), stejně jako 16 XMM nebo YMM zaregistruje k dispozici pro použití s plovoucí desetinnou čárkou. Volatile registrů se předpokládá, že volající, který se má zničit prostřednictvím volání pomocné registrů. Stálé registry je potřeba zachovat jejich hodnoty prostřednictvím volání funkce a musí být uložen volaný, pokud se používá.

### <a name="register-volatility-and-preservation"></a>Zaregistrujte volatility a zachovávání s rozlišením

Následující tabulka popisuje, jak každý registr se používá ve volání funkce:

||||
|-|-|-|
|Registr|Stav|Použití|
|RAX|Volatile|Návratová hodnota registru|
|RCX|Volatile|První argument typu celé číslo|
|RDX|Volatile|Druhý argument typu celé číslo|
|R8|Volatile|Třetí argument typu celé číslo|
|R9|Volatile|Čtvrtý argument typu celé číslo|
|R10:R11|Volatile|Musí být zachovány podle potřeby volajícím; používá se v pokynech syscall/sysret|
|R12:R15|Stálé|Musí být zachovány volaným|
|RDI|Stálé|Musí být zachovány volaným|
|RSI|Stálé|Musí být zachovány volaným|
|RBX|Stálé|Musí být zachovány volaným|
|RBP|Stálé|Může sloužit jako ukazatel na rámec; musí být zachovány volaným|
|RSP|Stálé|Ukazatel zásobníku|
|XMM0, YMM0|Volatile|První argument FP první argument typu vector při `__vectorcall` slouží|
|XMM1, YMM1|Volatile|Druhý argument FP; druhý argument typ vektoru při `__vectorcall` slouží|
|XMM2, YMM2|Volatile|Třetí argument FP třetí argument typ vektoru při `__vectorcall` slouží|
|XMM3, YMM3|Volatile|Čtvrtý argument FP čtvrtý argument typ vektoru při `__vectorcall` slouží|
|XMM4, YMM4|Volatile|Musí být zachovány podle potřeby volajícím; pátý argument typ vektoru při `__vectorcall` slouží|
|XMM5, YMM5|Volatile|Musí být zachovány podle potřeby volajícím; šestý argument typ vektoru při `__vectorcall` slouží|
|XMM6:XMM15, YMM6:YMM15|Stálé (XMM) Volatile (horní polovinu YMM)|Musí být zachovány volaným. Podle potřeby volající musí být zachovány registrech YMM.|

Při ukončení funkce a na položku funkce a volání knihovny Runtime jazyka C a systému Windows, příznak směru v procesoru příznaky registrace má zůstat nezaškrtnutá.

## <a name="stack-usage"></a>Použití zásobníku

Podrobnosti o přidělení zásobníku, zarovnání, typy funkcí a rámce zásobníku v x64 najdete v tématu [x64 zásobníku využití](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prolog a epilog

Každá funkce, která přiděluje místo v zásobníku volání dalších funkcí, ukládá stálé registry a používá zpracování výjimek musí mít prologu, jejíž adresa omezení jsou popsány v unwind data přidružená k příslušné funkce záznam tabulky a epilogu funkce v Každý konec funkce. Podrobnosti o požadované sekvence prologu a epilogu na x64 najdete v tématu [x64 sekvence prologu a epilogu](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>x64 zpracování výjimek

Informace o vytváření a datových struktur používaný k implementaci zpracování strukturovaných výjimek a chování x64 zpracování výjimek jazyka C++, naleznete v tématu [x64 zpracování výjimek](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení

Jeden omezení x64 kompilátoru je vložený assembler nepodporují. To znamená, že funkce, které nelze zapsat do jazyka C nebo C++ se buď musí být napsány podprogramy nebo jako vnitřní funkce podporovány kompilátorem. Některé funkce jsou citlivé na výkon, některé nikoli. Citlivé na výkon funkce by měla být implementována jako vnitřní funkce.

Vnitřní objekty podporovány kompilátorem jsou popsány v [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Formát obrázku

X64 formátu spustitelná image, která je typu PE32 +. Spustitelné bitové kopie (knihovny DLL a exe) jsou omezena na maximální velikosti 2 GB, takže relativní adresy s 32bitovým posunem můžete používat k adresování statických dat bitové kopie. Tato data zahrnují tabulky importních adres, řetězcové konstanty, statické globálních dat a tak dále.

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)
