---
title: override – specifikátor
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 71505f8b9b4dc2800e80a78a64f0ca6984af1349
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345872"
---
# <a name="override-specifier"></a>override – specifikátor

Můžete použít **přepsat** – klíčové slovo k určení členských funkcí, které přepíšou virtuální funkci v základní třídě.

## <a name="syntax"></a>Syntaxe

```
function-declaration override;
```

## <a name="remarks"></a>Poznámky

**Přepsat** je kontextový a má zvláštní význam pouze tehdy, když se používá po deklaraci členské funkce; v opačném případě to není rezervované klíčové slovo.

## <a name="example"></a>Příklad

Použití **přepsat** zabránit neúmyslnému chování dědičnosti ve vašem kódu. Následující příklad ukazuje, kde bez použití **přepsat**, nemusí je žádoucí chování členské funkce odvozené třídy. Kompilátor nebude posílat žádné chyby pro tento kód.

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

Při použití **přepsat**, kompilátor vygeneruje chyby tichého vytváření nové členské funkce.

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

Chcete-li určit, že funkce nelze přepsat a že nelze dědit třídy, použijte [konečné](../cpp/final-specifier.md) – klíčové slovo.

## <a name="see-also"></a>Viz také:

[final – specifikátor](../cpp/final-specifier.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)