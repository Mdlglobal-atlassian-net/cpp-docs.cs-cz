---
title: "Přehled členských funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6389197119135e7e800a4f5ec142bf42b1ef6d39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-member-functions"></a>Přehled členských funkcí
Členské funkce jsou statické nebo nestatické. Chování statické členské funkce se liší od jiných členské funkce, protože žádná implicitní statické členské funkce **to** argument. Nestatické členské funkce mají **to** ukazatel. Členské funkce, statické i nestatické, lze definovat v deklaraci třídy nebo mimo ni.  
  
 Pokud je členská funkce definována uvnitř deklarace třídy, považuje se za vloženou funkci a není potřeba kvalifikovat název funkce pomocí názvu třídy. I když funkcí definovaných v deklaracích třídy jsou již považovány za vložené funkce, můžete použít **vložené** – klíčové slovo dokumentu kódu.  
  
 Následuje příklad deklarování funkce v deklaraci třídy:  
  
```  
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
  
 Pokud definice členské funkce mimo deklaraci třídy, se zpracovává jako vložená funkce pouze v případě, že je explicitně deklarován jako **vložené**. Kromě toho musí být název funkce v definici kvalifikován názvem třídy pomocí operátoru rozlišení oboru (`::`).  
  
 V následujícím příkladu je deklarace třídy `Account` stejná jako předchozí deklarace této třídy s tím rozdílem, že je funkce `Deposit` definována mimo deklaraci třídy:  
  
```  
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
>  Ačkoli lze členské funkce definovat uvnitř deklarace třídy nebo samostatně, po definování třídy již nelze do této třídy přidat žádné další členské funkce.  
  
 Třídy obsahující členské funkce mohou mít mnoho deklarací, ale samotné členské funkce musejí být v programu definovány pouze jednou. Více definic vygeneruje v době propojování chybovou zprávu. Pokud třída obsahuje definice vložené funkce, musejí být definice této funkce shodné z důvodu tohoto pravidla „jedné definice“.  
  
