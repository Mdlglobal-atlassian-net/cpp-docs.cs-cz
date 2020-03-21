---
title: Zarovnání
description: Způsob, jakým je zarovnání dat C++určeno v moderních.
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 45b22742394a0b1c159e8b8102a26802a2441929
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076117"
---
# <a name="alignment"></a>Zarovnání

Jednou z funkcí nižší úrovně C++ je možnost určit přesné zarovnání objektů v paměti, aby bylo možné využít maximální využití konkrétní hardwarové architektury. Ve výchozím nastavení kompilátor zarovnává členy třídy a struktury s hodnotou velikosti: `bool` a `char` na hranici 1 bajtu, `short` na hranicích se dvěma bajty, `int`, `long`a `float` na hranicích se 4 bajty a `long long`, `double`a `long double` na hranici 8 bajtů.

Ve většině scénářů nikdy nemusíte mít obavy o zarovnání, protože výchozí zarovnání je již optimální. V některých případech ale můžete dosáhnout výrazného zvýšení výkonu nebo úspory paměti tím, že zadáte vlastní zarovnání vašich datových struktur. Před Visual Studio 2015 můžete použít klíčová slova specifická pro společnost Microsoft `__alignof` a `declspec(alignas)` k určení zarovnání většího, než je výchozí hodnota. Počínaje verzí Visual Studio 2015 byste měli použít standardní klíčová slova C++ 11 **alignof** a **alignas** pro maximální přenositelnost kódu. Nová klíčová slova se chovají stejným způsobem jako v digestoři jako rozšíření specifická pro společnost Microsoft. Dokumentace pro tato rozšíření platí také pro nová klíčová slova. Další informace najdete v tématu [operátor](../cpp/alignof-operator.md) a [Zarovnání](../cpp/align-cpp.md)__alignof. C++ Standard neurčuje chování při sbalení pro zarovnání na hranicích menších, než je výchozí kompilátor pro cílovou platformu, takže v takovém případě je stále nutné použít sadu Microsoft #pragma [Pack](../preprocessor/pack.md) .

Pro přidělení paměti datových struktur s vlastními zarovnáními použijte [třídu aligned_storage](../standard-library/aligned-storage-class.md) . [Třída aligned_union](../standard-library/aligned-union-class.md) slouží k určení zarovnání pro sjednocení s netriviálními konstruktory nebo destruktory.

## <a name="alignment-and-memory-addresses"></a>Zarovnání a adresy paměti

Zarovnání je vlastnost adresy paměti vyjádřená jako číselná adresa modulo 2. Například adresa 0x0001103F modulo 4 je 3. Tato adresa se označuje jako zarovnaná na 4n + 3, kde 4 značí zvolenou mocninu 2. Zarovnání adresy závisí na zvolené mocnině 2. Stejná adresa modulo 8 je 7. Adresa je označována jako zarovnaná na X, pokud je jeho zarovnání Xn + 0.

CPU spouští instrukce, které pracují s daty uloženými v paměti. Data jsou identifikována svými adresami v paměti. Každé datum má také velikost. Zavoláme k němu *přirozeně zarovnané* , pokud je jeho adresa zarovnaná na jeho velikost. V opačném případě se nazývá *nesprávně* navýšení. Například datum desetinné čárky s plovoucí desetinnou čárkou je přirozeně zarovnané, pokud adresa použitá k identifikaci má 8bitové zarovnání.

## <a name="compiler-handling-of-data-alignment"></a>Zpracování zarovnání dat kompilátorem

Kompilátory se snaží vytvořit data způsobem, který zabraňuje chybnému zarovnání dat.

Pro jednoduché datové typy kompilátor přiřadí adresy, které jsou násobky velikosti v bajtech datového typu. Kompilátor například přiřadí adresy proměnným typu `long`, které jsou násobky 4, nastavení dolních 2 bitů adresy na nulu.

Kompilátor také Zapad struktury způsobem, který přirozeně zarovnává každý prvek struktury. Vezměte v úvahu `struct x_` struktury v následujícím příkladu kódu:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

Kompilátor vyplní tuto strukturu, aby se vynutilo zarovnání přirozeně.

Následující příklad kódu ukazuje, jak kompilátor umístí čalouněnou strukturu do paměti:

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

Obě deklarace vrací `sizeof(struct x_)` jako 12 bajtů.

Druhá deklarace obsahuje dva prvky odsazení:

1. `char _pad0[3]` pro zarovnávání `int b` členů na hranici 4 bajtů.

1. `char _pad1[1]` pro zarovnání prvků pole struktury `struct _x bar[3];` na hranici se čtyřmi bajty.

Odsazení zarovnává prvky `bar[3]` způsobem, který umožňuje přirozený přístup.

Následující příklad kódu ukazuje `bar[3]` rozložení pole:

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="alignof-and-alignas"></a>alignof a alignas

Specifikátor typu **alignas** je přenosný, standardní způsob C++ , jak určit vlastní zarovnání proměnných a uživatelsky definovaných typů. Operátor **alignof** je podobně jako standardní, přenosný způsob, jak získat zarovnání zadaného typu nebo proměnné.

## <a name="example"></a>Příklad

**Alignas** můžete použít pro třídu, strukturu nebo sjednocení nebo pro jednotlivé členy. Pokud je nalezeno více specifikátorů **alignas** , kompilátor zvolí nejpřísnější z nich (ten s největší hodnotou).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Viz také

[Zarovnání struktury dat](https://en.wikipedia.org/wiki/Data_structure_alignment)
