---
title: final – specifikátor
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 93e8d9b0b445d1120ec15911eb763ae1d7d2d359
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188651"
---
# <a name="final-specifier"></a>final – specifikátor

Pomocí klíčového slova **Final** můžete určit virtuální funkce, které nelze přepsat v odvozené třídě. Lze jej také použít k označení tříd, ze kterých nelze dědit.

## <a name="syntax"></a>Syntaxe

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Poznámky

**konečný** kontext rozlišuje a má zvláštní význam pouze v případě, že se používá po deklaraci funkce nebo názvu třídy; jinak se nejedná o rezervované klíčové slovo.

Pokud je v deklaracích třídy použit **konečný** , `base-classes` je volitelná část deklarace.

## <a name="example"></a>Příklad

Následující příklad používá **konečné** klíčové slovo k určení, že virtuální funkci nelze přepsat.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

Informace o tom, jak určit, že členské funkce mohou být přepsány, naleznete v tématu [specifikátor override](../cpp/override-specifier.md).

Následující příklad používá **konečné** klíčové slovo k určení, že třídu nelze zdědit.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[override – specifikátor](../cpp/override-specifier.md)
