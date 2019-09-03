---
title: warning – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: 9a79f0c4a9eed6b62e42f056f9d1994b44b57297
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216469"
---
# <a name="warning-pragma"></a>warning – direktiva pragma

Povoluje selektivní úpravu chování zpráv s upozorněním kompilátoru.

## <a name="syntax"></a>Syntaxe

> **upozornění #pragma (** \
> &nbsp;&nbsp;&nbsp;&nbsp;*Upozornění – specifikátor* **:** *Upozornění-číslo-seznam*\
> &nbsp;&nbsp;&nbsp;&nbsp;[ **;** *Upozornění – specifikátor* **:** *Upozornění-číslo-seznam* ...] **)** \
> **upozornění #pragma (push** [ **,** *n* ] **)** \
> **upozornění #pragma (pop)**

## <a name="remarks"></a>Poznámky

K dispozici jsou následující parametry specifikátoru upozornění.

|Upozornění – specifikátor|Význam|
|------------------------|-------------|
|*1, 2, 3, 4*|Použije danou úroveň na určená upozornění. Také zapne zadané upozornění, které je ve výchozím nastavení vypnuté.|
|*default*|Resetovat chování upozornění na jeho výchozí hodnotu. Také zapne zadané upozornění, které je ve výchozím nastavení vypnuté. Upozornění bude vygenerováno ve výchozí dokumentované úrovni.<br /><br /> Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*disable*|Neprovádějte zadané zprávy s varováním.|
|*Chyba*|Oznamovat zadaná upozornění jako chyby.|
|*once*|Zobrazí zadané zprávy pouze jednou.|
|*tlačí*|Posune aktuální stav direktivy pragma v zásobníku, zakáže zadané upozornění pro další řádek a potom se zaznamená do zásobníku upozornění tak, aby byl obnoven stav direktivy pragma.|

Následující příkaz kódu ilustruje, že `warning-number-list` parametr může obsahovat více čísel upozornění a že více `warning-specifier` parametrů lze zadat ve stejné direktivě pragma.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Tato direktiva je funkčně ekvivalentní následujícímu kódu:

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

Kompilátor přidá 4000 k jakémukoli číslu upozornění, které je mezi 0 a 999.

Pro čísla upozornění v rozsahu 4700-4999, které jsou spojeny s generováním kódu, je stav upozornění v účinnosti, když kompilátor narazí na levou složenou závorku funkce, bude platit pro zbytek funkce. Pokud chcete změnit stav upozornění, které je větší než 4699, použijte direktivu pragma **Warning** ve funkci, která se projeví až po konci funkce. Následující příklad ukazuje správné umístění direktiv pragma **Upozornění** pro zakázání zprávy upozornění generování kódu a pak je obnovit.

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

Všimněte si, že v těle funkce bude poslední nastavení pro celou funkci platit jako poslední.

## <a name="push-and-pop"></a>Push a pop

Direktiva pragma **Warning** také podporuje následující syntaxi, kde *n* představuje úroveň upozornění (1 až 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Direktiva `warning( push )` pragma ukládá aktuální stav varování pro každé upozornění. Direktiva `warning( push, n )` pragma ukládá aktuální stav pro každé upozornění a nastaví globální úroveň upozornění na *n*.

Direktiva `warning( pop )` pragma vyvolá poslední stav upozornění, který byl vložen do zásobníku. Všechny změny, které jste provedli ve stavu upozornění mezi vložením a *POP* , jsou vráceny zpět. Vezměte v úvahu tento příklad:

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

Na konci tohoto kódu obnoví příkaz *POP* stav každého upozornění (zahrnuje 4705, 4706 a 4707) na to, co bylo na začátku kódu.

Při zápisu hlavičkových souborů můžete použít příkaz *push* a *POP* k zajištění, že změny stavu upozornění provedené uživatelem nebrání správnému kompilování hlaviček. Použijte *nabízení* na začátku hlavičky a na konci . Například pokud máte hlavičku, která se čistě zkompiluje na úrovni upozornění 4, následující kód změní úroveň upozornění na 3 a pak obnoví původní úroveň upozornění na konci hlavičky.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Další informace o možnostech kompilátoru, které vám pomůžou potlačit upozornění, najdete v tématu [/Fi](../build/reference/fi-name-forced-include-file.md) a [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
