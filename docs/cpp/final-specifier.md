---
title: final – specifikátor
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: c6400c8060664713fdd004a5aa9536e0617bc0c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588081"
---
# <a name="final-specifier"></a>final – specifikátor

Můžete použít **konečné** – klíčové slovo pro označení virtuálních funkcí, které nelze přepsat v odvozené třídě. Lze jej také použít k označení tříd, ze kterých nelze dědit.

## <a name="syntax"></a>Syntaxe

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Poznámky

**poslední** je kontextový a má zvláštní význam, jen když se používá po deklaraci funkce nebo názvu třídy, jinak, to není rezervované klíčové slovo.

Když **konečné** se používá v deklaracích třídy `base-classes` volitelnou částí deklarace.

## <a name="example"></a>Příklad

V následujícím příkladu **konečné** – klíčové slovo k určení toho, že virtuální funkci nelze přepsat.

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

Informace o tom, jak určit, že můžete členské funkce přepsat, naleznete v tématu [specifikátor override](../cpp/override-specifier.md).

Následující příklad používá **konečné** – klíčové slovo k určení, zda třídu nelze zdědit.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[override – specifikátor](../cpp/override-specifier.md)