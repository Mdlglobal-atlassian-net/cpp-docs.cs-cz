---
title: x64 – softwarové konvence
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417192"
---
# <a name="x64-software-conventions"></a>x64 – softwarové konvence

Tato část popisuje metodologii konvence C++ volání pro x64, 64 rozšíření na architekturu x86.

## <a name="overview-of-x64-calling-conventions"></a>Přehled konvencí volání x64

Mezi dva důležité rozdíly mezi x86 a x64 patří možnost adresování 64 a plochá sada 16 64 bitových registrů pro obecné použití. V případě rozšířené sady registru používá platforma x64 konvenci volání [__fastcall](../cpp/fastcall.md) a model zpracování výjimek založený na platformě RISC. `__fastcall` konvence používá registry pro první čtyři argumenty a rámec zásobníku k předání dalších argumentů. Podrobnosti o konvenci volání x64, včetně použití registru, parametrů zásobníku, návratových hodnot a uvolnění zásobníku, najdete v tématu [konvence volání x64](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Povolit optimalizaci pro x64

Následující možnost kompilátoru vám pomůže optimalizovat aplikaci pro platformu x64:

- [/favor (optimalizace pro konkrétní architekturu)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Typy a úložiště

Tato část popisuje výčet a úložiště datových typů pro architekturu x64.

### <a name="scalar-types"></a>Skalární typy

I když je možné získat přístup k datům s jakýmkoli zarovnáním, doporučujeme zarovnat data na své přirozené hranici nebo několik více, aby nedošlo ke ztrátě výkonu. Výčty jsou konstantní celá čísla a jsou považovány za 32 celá čísla. Následující tabulka popisuje definice typu a doporučené úložiště pro data, která se týkají zarovnání pomocí následujících hodnot zarovnání:

- Bity-8 bitů

- Bity aplikace Word-16

- Doubleword – 32 bitů

- Quadword – 64 bitů

- Octaword – 128 bitů

|||||
|-|-|-|-|
|Skalární typ|Datový typ C|Velikost úložiště (v bajtech)|Doporučené zarovnání|
|**INT8**|**char**|1|Byte|
|**UINT8**|**znak bez znaménka**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**krátký unsigned**|2|Word|
|**UVEDENA**|**int**, **Long**|4|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|4|Doubleword|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**Nepodepsaný __int64**|8|Quadword|
|**FP32 (jednoduchá přesnost)**|**float**|4|Doubleword|
|**FP64 (dvojitá přesnost)**|**double**|8|Quadword|
|**UKAZATELE**|__\*__|8|Quadword|
|**__m64**|**__m64 struktury**|8|Quadword|
|**__m128**|**__m128 struktury**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agregace a sjednocení

Jiné typy, například pole, struktury a sjednocení, mají přísnější požadavky na zarovnání, které zajišťují konzistentní a sjednocení úložiště a načítání dat. Tady jsou definice pro pole, strukturu a sjednocení:

- Pole

   Obsahuje uspořádanou skupinu sousedních datových objektů. Každý objekt se nazývá *element*. Všechny prvky v poli mají stejnou velikost a datový typ.

- Struktura

   Obsahuje uspořádanou skupinu datových objektů. Na rozdíl od prvků pole, datové objekty v rámci struktury mohou mít různé datové typy a velikosti. Každý datový objekt ve struktuře se nazývá *člen*.

- Sjednocení

   Objekt, který obsahuje některý ze sady pojmenovaných členů. Členové pojmenované sady mohou být libovolného typu. Úložiště přidělené pro sjednocení je stejné jako úložiště požadované pro největšího člena tohoto sjednocení a jakékoli odsazení nutné pro zarovnání.

Následující tabulka ukazuje silné navrhované zarovnání skalárních členů sjednocení a struktur.

||||
|-|-|-|
|Skalární typ|Datový typ C|Vyžadované zarovnání|
|**INT8**|**char**|Byte|
|**UINT8**|**znak bez znaménka**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**krátký unsigned**|Word|
|**UVEDENA**|**int**, **Long**|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|Doubleword|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**Nepodepsaný __int64**|Quadword|
|**FP32 (jednoduchá přesnost)**|**float**|Doubleword|
|**FP64 (dvojitá přesnost)**|**double**|Quadword|
|**UKAZATELE**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 struktury**|Quadword|
|**__m128**|**__m128 struktury**|Octaword|

Platí následující pravidla agregovaného zarovnání:

- Zarovnání pole je stejné jako zarovnání jednoho z prvků pole.

- Zarovnání začátku struktury nebo sjednocení je maximální zarovnání kteréhokoli jednotlivého člena. Každý člen v rámci struktury nebo sjednocení je nutné umístit na správné zarovnání, jak je definováno v předchozí tabulce, což může vyžadovat implicitní vnitřní odsazení v závislosti na předchozím členu.

- Velikost struktury musí být celočíselná násobek jeho zarovnání, což může vyžadovat odsazení za posledním členem. Vzhledem k tomu, že struktury a sjednocení mohou být seskupeny do polí, musí každý prvek pole struktury nebo sjednocení začínat a končit správným zarovnáním dříve stanoveným.

- Je možné zarovnávat data tak, aby byla větší než požadavky na zarovnání, pokud jsou zachována předchozí pravidla.

- Jednotlivé kompilátory mohou upravit balení struktury z důvodu velikosti. Například [/zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md) umožňuje úpravu balení struktur.

### <a name="examples-of-structure-alignment"></a>Příklady zarovnání struktur

Následující čtyři příklady každé deklaruje zarovnaná strukturu nebo sjednocení a příslušné hodnoty ilustrují rozložení této struktury nebo sjednocení v paměti. Každý sloupec na obrázku představuje bajt paměti a číslo ve sloupci označuje posunutí daného bajtu. Název v druhém řádku každého obrázku odpovídá názvu proměnné v deklaraci. Šedivé sloupce označují odsazení, které je požadováno k dosažení zadaného zarovnání.

#### <a name="example-1"></a>Příklad 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Rozložení pro převod AMD – příklad struktury 1](../build/media/vcamd_conv_ex_1_block.png "Rozložení pro převod AMD – příklad struktury 1")

#### <a name="example-2"></a>Příklad 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Ukázka převodu AMD 2 rozvržení struktury](../build/media/vcamd_conv_ex_2_block.png "Ukázka převodu AMD 2 rozvržení struktury")

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

![Ukázka převodu AMD 2 rozvržení struktury](../build/media/vcamd_conv_ex_3_block.png "Ukázka převodu AMD 2 rozvržení struktury")

#### <a name="example-4"></a>Příklad 4:

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Příklad převodu AMD 4 sjednocení layouit](../build/media/vcamd_conv_ex_4_block.png "Příklad převodu AMD 4 sjednocení layouit")

### <a name="bitfields"></a>Bitová pole

Bitová pole struktury jsou omezená na 64 bitů a můžou být typu signed int, unsigned int, Int64 nebo unsigned Int64. Bitová pole, která překračují hranice typu, přeskočí bity, aby zarovnaly bitového pole k dalšímu zarovnání typu. Například celočíselná bitová pole nesmí překročit 32-bit boundry.

### <a name="conflicts-with-the-x86-compiler"></a>Konflikty s kompilátorem x86

Datové typy, které jsou větší než 4 bajty, nejsou v zásobníku automaticky zarovnány při použití kompilátoru x86 ke kompilaci aplikace. Vzhledem k tomu, že architektura pro kompilátor x86 má 4 bajty zarovnaných bajtů, může být například hodnota, která je větší než 4 bajty, třeba 64 celé číslo, automaticky zarovnána na 8 bajtů.

Práce s zarovnanými daty má dva důsledky.

- Přístup k zarovnaným umístěním může trvat déle než při přístupu k zarovnaným místům.

- V propojených operacích nelze použít nezarovnané umístění.

Pokud potřebujete přísnější zarovnání, použijte `__declspec(align(N))` v deklaracích proměnných. To způsobí, že kompilátor dynamicky zarovnává zásobník tak, aby splňoval vaše specifikace. Nicméně dynamická úprava zásobníku v době běhu může způsobit pomalejší provádění aplikace.

## <a name="register-usage"></a>Využití registrů

Architektura x64 poskytuje pro 16 – registry pro obecné účely (označované jako Registry typu Integer) a také 16 XMM/YMM Registry k dispozici pro použití s plovoucí desetinnou čárkou. Nestálé Registry jsou pomocné Registry očekávané volajícím pro zničení v rámci volání. Nestálé Registry jsou požadovány pro uchování jejich hodnot napříč voláním funkce a musí být uloženy volaným, pokud je použit.

### <a name="register-volatility-and-preservation"></a>Registrovat nestálost a zachování

Následující tabulka popisuje, jak se každý registr používá napříč voláními funkcí:

||||
|-|-|-|
|Registrace|Stav|Použití|
|RAX|Permanentní|Registr návratových hodnot|
|RCX|Permanentní|První celočíselný argument|
|RDX|Permanentní|Druhý celočíselný argument|
|R8|Permanentní|Třetí celočíselný argument|
|R9|Permanentní|Čtvrtý celočíselný argument|
|R10:R11|Permanentní|Musí být zachováno podle potřeby volajícím; používá se v pokynech pro syscall/sysret.|
|R12:R15|Stálé|Musí být zachováno volaným|
|RDI|Stálé|Musí být zachováno volaným|
|RSI|Stálé|Musí být zachováno volaným|
|RBX|Stálé|Musí být zachováno volaným|
|RBP|Stálé|Dá se použít jako ukazatel na rámec; musí být zachováno volaným|
|RSP|Stálé|Ukazatel zásobníku|
|XMM0, YMM0|Permanentní|První argument FP; první argument typu vector, když se používá `__vectorcall`|
|XMM1, YMM1|Permanentní|Druhý argument FP; druhý argument typu vector, když se používá `__vectorcall`|
|XMM2, YMM2|Permanentní|Třetí argument FP; třetí argument typu vector, když se používá `__vectorcall`|
|XMM3, YMM3|Permanentní|Čtvrtý argument FP; čtvrtý argument typu vector, když se používá `__vectorcall`|
|XMM4, YMM4|Permanentní|Musí být zachováno podle potřeby volajícím; pátý argument typu vector, když se používá `__vectorcall`|
|XMM5, YMM5|Permanentní|Musí být zachováno podle potřeby volajícím; Šestý argument typu vector, když se používá `__vectorcall`|
|XMM6:XMM15, YMM6:YMM15|Nevolatile (XMM), volatile (horní polovina YMM)|Musí být zachováno volaným. YMM Registry musí být zachovány podle potřeby volajícím.|

Při ukončení funkce a při vstupu funkce na volání knihovny běhového prostředí C a volání systému Windows se očekává, že příznak směru v registru příznaků procesoru bude vymazán.

## <a name="stack-usage"></a>Využití zásobníku

Podrobnosti o přidělování, zarovnání, typech funkcí a snímcích zásobníku na platformě x64 najdete v tématu [použití zásobníku x64](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prolog a epilog

Každá funkce, která přiděluje místo v zásobníku, volá jiné funkce, ukládá nestálé registry nebo používá zpracování výjimek, musí mít prolog, jehož omezení adresy jsou popsána v části unwind data přidružená k příslušné položce tabulky funkcí a epilogy na adrese. každý výstup do funkce. Podrobnosti o požadovaném kódu prologu a epilogu na platformě x64 naleznete v tématu [prolog a epilog x64](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>x64 – ošetření výjimek

Informace o konvencích a datových strukturách, které se používají k implementaci strukturovaného zpracování výjimek a C++ chování zpracování výjimek v x64, naleznete v tématu [zpracování výjimek x64](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení

Jedním z omezení pro kompilátor x64 je, že neexistují žádná vložená podpora assembleru. To znamená, že funkce, které nemohou být zapsány v jazyce C nebo C++ budou buď muset být zapsány jako podrutiny, nebo jako vnitřní funkce podporované kompilátorem. Některé funkce jsou citlivé na výkon, zatímco jiné nejsou. Funkce citlivé na výkon by měly být implementovány jako vnitřní funkce.

Vnitřní objekty podporované kompilátorem jsou popsány v tématu [vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Formát obrázku

Formát spustitelného obrazu x64 je PE32 +. Spustitelné Image (knihovny DLL i exe) jsou omezené na maximální velikost 2 gigabajty, takže relativní adresování s 32 bity se dá použít k adresování statických obrazových dat. Tato data zahrnují tabulku importních adres, řetězcové konstanty, statická globální data a tak dále.

## <a name="see-also"></a>Viz také

[Konvence volání](../cpp/calling-conventions.md)
