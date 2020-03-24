---
title: override – specifikátor
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188477"
---
# <a name="override-specifier"></a>override – specifikátor

Můžete použít klíčové slovo **override** k určení členských funkcí, které přepíší virtuální funkci v základní třídě.

## <a name="syntax"></a>Syntaxe

```
function-declaration override;
```

## <a name="remarks"></a>Poznámky

**přepsání** je kontextově závislé a má zvláštní význam pouze v případě, že se používá po deklaraci členské funkce; jinak se nejedná o rezervované klíčové slovo.

## <a name="example"></a>Příklad

Pomocí **přepsání** můžete zabránit nechtěnému chování dědění ve vašem kódu. Následující příklad ukazuje, kde bez použití **override**není chování členské funkce odvozené třídy zamýšlené. Kompilátor negeneruje žádné chyby pro tento kód.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

Při použití **override**kompilátor generuje chyby namísto tichého vytváření nových členských funkcí.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

Chcete-li určit, že funkce nelze přepsat a že třídy nelze dědit, použijte klíčové slovo [Final](../cpp/final-specifier.md) .

## <a name="see-also"></a>Viz také

[final – specifikátor](../cpp/final-specifier.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
