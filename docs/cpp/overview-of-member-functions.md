---
title: Přehled členských funkcí
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: 6dec4ee53cd840c47d76ac0579daca710b0eeb68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358410"
---
# <a name="overview-of-member-functions"></a>Přehled členských funkcí

Členské funkce jsou statické nebo nestatické. Chování statických členských funkcí se liší od ostatních členských funkcí, protože statické členské funkce nemají implicitní **tento** argument. Nestatické členské funkce mají **tento** ukazatel. Členské funkce, statické i nestatické, lze definovat v deklaraci třídy nebo mimo ni.

Pokud je členská funkce definována uvnitř deklarace třídy, považuje se za vloženou funkci a není potřeba kvalifikovat název funkce pomocí názvu třídy. Přestože funkce definované uvnitř deklarace třídy jsou již považovány za vložených funkcí, můžete použít **vložených** klíčových slov pro kód dokumentu.

Následuje příklad deklarování funkce v deklaraci třídy:

```cpp
// overview_of_member_functions1.cpp
class Account
{
public:
    // Declare the member function Deposit within the declaration
    //  of class Account.
    double Deposit( double HowMuch )
    {
        balance += HowMuch;
        return balance;
    }
private:
    double balance;
};

int main()
{
}
```

Pokud definice členské funkce je mimo deklaraci třídy, je považována za vložkou pouze v případě, že je explicitně deklarována jako **inline**. Kromě toho musí být název funkce v definici kvalifikován názvem třídy pomocí operátoru rozlišení oboru (`::`).

V následujícím příkladu je deklarace třídy `Account` stejná jako předchozí deklarace této třídy s tím rozdílem, že je funkce `Deposit` definována mimo deklaraci třídy:

```cpp
// overview_of_member_functions2.cpp
class Account
{
public:
    // Declare the member function Deposit but do not define it.
    double Deposit( double HowMuch );
private:
    double balance;
};

inline double Account::Deposit( double HowMuch )
{
    balance += HowMuch;
    return balance;
}

int main()
{
}
```

> [!NOTE]
> Ačkoli lze členské funkce definovat uvnitř deklarace třídy nebo samostatně, po definování třídy již nelze do této třídy přidat žádné další členské funkce.

Třídy obsahující členské funkce mohou mít mnoho deklarací, ale samotné členské funkce musejí být v programu definovány pouze jednou. Více definic vygeneruje v době propojování chybovou zprávu. Pokud třída obsahuje definice vložené funkce, musejí být definice této funkce shodné z důvodu tohoto pravidla „jedné definice“.
