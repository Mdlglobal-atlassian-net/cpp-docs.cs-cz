---
title: upozornění
ms.date: 11/04/2016
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: 1341472af22582635207a2bdff93b4367fd59330
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179929"
---
# <a name="warning-pragma"></a>– Direktiva Pragma upozornění
Umožňuje selektivní úpravy chování zprávy upozornění kompilátoru.

## <a name="syntax"></a>Syntaxe

```
#pragma warning(
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )
#pragma warning( push[ ,n ] )
#pragma warning( pop )
```

## <a name="remarks"></a>Poznámky

K dispozici jsou následující parametry upozornění specifier.

|upozornění – specifikátor|Význam|
|------------------------|-------------|
|*1, 2, 3, 4*|Platí pro zadaný počet upozornění: na dané úrovni. To také zapne zadané upozornění, která je ve výchozím nastavení vypnuté.|
|*default*|Chování upozornění resetovat na výchozí hodnotu. To také zapne zadané upozornění, která je ve výchozím nastavení vypnuté. Upozornění se vygeneruje při jeho výchozí, zdokumentovat, úroveň.<br /><br /> Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*disable*|Zadaná zpráva nebo zprávy upozornění bez vyvolání.|
|*error*|Sestavy určených upozornění jako chyby.|
|*once*|Zobrazení zadané zprávy pouze jednou.|
|*potlačení*|Posune aktuální stav direktivy pragma v zásobníku, zakáže zadané upozornění pro další řádek a potom zobrazí zásobník upozornění tak, aby se resetuje stav direktivy pragma.|

Příkaz následující kód ukazuje, že `warning-number-list` parametr může obsahovat více čísel upozornění a že více `warning-specifier` v stejné – Direktiva pragma lze zadat parametry.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Toto je funkčně srovnatelný s následujícím kódem.

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

Kompilátor přidá 4000 do libovolného počtu upozornění, která je od 0 do 999.

Pro upozornění čísla v rozsahu 4700 4999, které jsou ty, které jsou přidružené k generování kódu, stavu upozornění, výsledkem bude, když kompilátor narazí na otevřené složené závorky funkce, pro ostatní funkce nebudou platit. Použití **upozornění** – Direktiva pragma ve funkci změny stavu upozornění, že má číslo větší než 4699 se projeví až po konec funkce. Následující příklad ukazuje správné umístění **upozornění** direktivy pragma zakážete generování kódu upozornění a pak ho obnovit.

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

Všimněte si, že v rámci funkce textu, poslední nastavení **upozornění** – Direktiva pragma, nebudou platit pro celou funkci.

## <a name="push-and-pop"></a>Se službami push a vyvolat přes Pop

**Upozornění** – Direktiva pragma podporuje také následující syntaxi, kde *n* představuje úroveň pro upozornění (1 až 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Direktivy pragma `warning( push )` uloží aktuální stav varování u každé varování. Direktivy pragma `warning( push, n )` ukládá aktuální stav pro každé upozornění a nastaví globální úroveň pro upozornění na *n*.

Direktivy pragma `warning( pop )` POP poslední stav upozornění vloženy do zásobníku. Všechny změny provedené do stavu varování mezi *nabízených* a *pop* se vrátit zpět. Podívejte se například:

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

Na konci tohoto kódu *pop* obnoví stav každé varování (včetně 4705 4706 a 4707) který byl při spuštění kódu.

Při zápisu hlavičkové soubory, můžete použít *nabízených* a *pop* zaručí, že stav varování změny provedené uživatelem nezabrání hlavičky kompilaci správně. Použití *nabízených* na začátku záhlaví a *pop* na konci. Například pokud máte hlavičku, která není čistě kompilace na úroveň upozornění 4, následující kód by změnit úroveň upozornění 3 a obnovte původní úroveň pro upozornění na konci záhlaví.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Další informace o kompilátoru, možnosti, které vám pomůžou potlačit upozornění, najdete v části [/FI](../build/reference/fi-name-forced-include-file.md) a [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)