---
title: pack
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: bf1ae81184d53dd271f63c26e8f9a52a6410b232
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038444"
---
# <a name="pack"></a>pack
Určuje zarovnání zabalení pro struktury, sjednocení a členy třídy.

## <a name="syntax"></a>Syntaxe

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>Parametry

**show**<br/>
(Volitelné) Zobrazí aktuální hodnotu bajtu pro balení zarovnání. Hodnota se zobrazí zpráva upozornění.

**push**<br/>
(Volitelné) Nabízená oznámení aktuální zarovnání zabalení hodnoty na vnitřního zásobníku kompilátoru a nastaví hodnotu aktuální zarovnání zabalení *n*. Pokud *n* není zadán, aktuální hodnota zarovnání zabalení je vloženo.

**pop**<br/>
(Volitelné) Odstraní záznam z vrcholu vnitřního zásobníku kompilátoru. Pokud *n* není zadaný s **pop**, balení hodnotu přidruženou k výsledného záznamu vrcholu zásobníku je nová hodnota zarovnání zabalení. Pokud *n* není zadána, například `#pragma pack(pop, 16)`, *n* stane nová hodnota zarovnání zabalení. Pokud jste vyvolat přes pop s *identifikátor*, například `#pragma pack(pop, r1)`, pak všechny záznamy v zásobníku jsou otevřené až do záznam, který má *identifikátor* nenajde. Že záznam není vyjmut záznam a přidružený výsledného záznamu v horní hodnota balení je zásobník nové balení hodnota zarovnání. Pokud jste vyvolat přes pop s *identifikátor* , který se nenachází v libovolné záznamu v zásobníku, pak bude **pop** se ignoruje.

*identifier*<br/>
(Volitelné) Při použití s *nabízených*, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. Při použití s **pop**, vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic nevezme.

*n*<br/>
(Volitelné) Určuje hodnotu, v bajtech, která má být použit pro balení. Pokud možnost kompilátoru [/zp](../build/reference/zp-struct-member-alignment.md) není nastaven pro modul, výchozí hodnota pro *n* je 8. Platné hodnoty jsou 1, 2, 4, 8 a 16. Zarovnání člena bude na hranici, která je buď jednat o násobek *n* nebo násobkem velikosti člena, podle toho, co je menší.

`#pragma pack(pop, identifier, n)` není definován.

## <a name="remarks"></a>Poznámky

Aby zabalil třídy, je umístit jejích členů přímo po sobě navzájem v paměti, což může znamenat, že některé nebo všechny členy může být zarovnány na hranice menší než výchozí zarovnání Cílová architektura. **balíček** poskytuje řízení na úrovni deklarace dat. Tím se liší od – možnost kompilátoru [/zp](../build/reference/zp-struct-member-alignment.md), které jen poskytuje řízení na úrovni modulu. **Pack** se projeví při prvním **struktura**, **sjednocení**, nebo **třídy** deklarace po direktivy pragma je zobrazena. **balíček** nemá žádný vliv na definice. Volání **pack** sadami žádné argumenty *n* na hodnotu nastavenou v možnosti kompilátoru `/Zp`. Pokud není nastavena možnost kompilátoru, výchozí hodnota je 8.

Pokud změníte zarovnání struktury, se nesmí používat jako uvidí ke snížení výkonu nebo dokonce i získat generované hardwarové výjimky nezarovnaný přístup, kolik místa v paměti, ale.  Tato výjimka chování lze upravit pomocí [SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621).

Další informace o úpravách zarovnání naleznete v následujících tématech:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Příklady zarovnání struktur](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64 konkrétní)

   > [!WARNING]
   > Všimněte si, že v sadě Visual Studio 2015 a novější můžete použít operátory alignof a alignas standardní které, na rozdíl od `__alignof` a `declspec( align )` přenositelnosti napříč kompilátory. Standard jazyka C++ neřeší balení, takže je nutné použít **pack** (nebo odpovídající rozšíření na jiné kompilátory) k určení zarovnání menší než velikost cílové architektury aplikace word.

## <a name="examples"></a>Příklady

Následující příklad ukazuje způsob použití **pack** – Direktiva pragma, chcete-li změnit zarovnání struktury.

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

Následující příklad ukazuje způsob použití *nabízených*, *pop*, a *zobrazit* syntaxe.

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)