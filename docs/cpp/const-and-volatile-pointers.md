---
title: "Ukazatelé const a volatile | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68089c80528265a4375767d9f0a744cb95cb970b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="const-and-volatile-pointers"></a>Ukazatelé const a volatile
[Const](../cpp/const-cpp.md) a [volatile](../cpp/volatile-cpp.md) klíčová slova změnit, jak jsou považovány ukazatele. **Const** – klíčové slovo určuje, zda je ukazatel nelze změnit po inicializaci; ukazatele je chráněna před změnou po tomto datu.  
  
 Klíčové slovo `volatile` určuje, že hodnotu přiřazenou k následujícímu názvu lze upravit akcemi i mimo aplikaci uživatele. Klíčové slovo `volatile` je proto užitečné k deklaraci objektů ve sdílené paměti, ke kterým může přistoupit několik procesů nebo oblastí globálních dat používaných pro komunikaci s rutinami služby přerušení.  
  
 Je-li název deklarován jako `volatile`, kompilátor jeho hodnotu znovu načte z paměti pokaždé, kdy k němu program přistoupí. Tím jsou výrazně omezeny možné optimalizace. Pokud však může dojít k nečekané změně stavu objektu, jde o jediný způsob, jak lze zajistit předvídatelný výkon programu.  
  
 Deklarovat objekt ukazuje ukazatel jako **const** nebo `volatile`, použijte deklaraci ve tvaru:  
  
```  
const char *cpch;  
volatile char *vpch;  
```  
  
 Deklarovat hodnota ukazatele – to znamená, Skutečná adresa, které jsou uložené v ukazatele – jako **const** nebo `volatile`, použijte deklaraci ve tvaru:  
  
```  
char * const pchc;  
char * volatile pchv;  
```  
  
 Jazyk C++ brání přiřazení, která umožňují úpravy objektu nebo ukazatel deklarován jako **const**. Taková přiřazení by odstranila informaci, s níž byl objekt nebo ukazatel deklarován, a porušila by tak záměr původní deklarace. Vezměte v úvahu následující deklarace:  
  
```  
const char cch = 'A';  
char ch = 'B';  
```  
  
 Zadané předchozí deklarace dvou objektů (`cch`, typu **const char**, a `ch`, typu **char)**, platí následující prohlášení nebo inicializacích:  
  
```  
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 Následující deklarace či inicializace jsou chybné.  
  
```  
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 Deklarace proměnné `pch2` deklaruje ukazatel, pomocí kterého lze upravit konstantní objekt, a proto není povolena. Deklarace proměnné `pch3` určuje, že ukazatel (`pointer`) je konstantní, nikoli objekt. Deklarace není povolena ze stejného důvodu, z jakého není povolena deklarace proměnné `pch2`.  
  
 Následujících osm přiřazení ukazuje přiřazování pomocí ukazatele a změnu hodnoty ukazatele z předchozích deklarací. Pro tuto chvíli předpokládejme, že pro proměnné `pch1` až `pch8` byla inicializace správná.  
  
```  
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 Ukazatele deklarován jako `volatile`, nebo jako směs **const** a `volatile`, orientují stejná pravidla.  
  
 Ukazatelé na **const** objekty se často používají v deklaracích funkce následujícím způsobem:  
  
```  
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 Předchozí příkaz deklaruje funkci, [strcpy_s –](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), kde jsou dva tři argumenty typu ukazatele na `char`. Protože jsou argumenty předávané odkazem a podle hodnoty, nebude funkce můžete změnit i `strDestination` a `strSource` Pokud `strSource` nebyly deklarován jako **const**. Prohlášení o `strSource` jako **const** zaručuje volající, který `strSource` nelze změnit pomocí příkazu volaná funkce.  
  
> [!NOTE]
>  Protože je standardní převod z *typename*  **\***  k **const** *typename*  **\*** , je možné předat argument typu **char \***  k [strcpy_s –](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Naopak však není true; neexistuje žádná implicitní převod odebrat **const** atribut z objektu nebo ukazatele.  
  
 A **const** ukazatel daného typu lze přiřadit k ukazatel stejného typu. Ukazatel, není však **const** nemůže být přiřazen, **const** ukazatel. Následující kód ukazuje správná i nesprávná přiřazení:  
  
```  
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 Následující příklad ukazuje, jak deklarovat objekt jako const, pracujete-li s ukazatelem na ukazatel na objekt.  
  
```  
// const_pointer2.cpp  
struct X {  
   X(int i) : m_i(i) { }  
   int m_i;  
};  
  
int main() {  
   // correct  
   const X cx(10);  
   const X * pcx = &cx;  
   const X ** ppcx = &pcx;  
  
   // also correct  
   X const cx2(20);  
   X const * pcx2 = &cx2;  
   X const ** ppcx2 = &pcx2;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Ukazatele](../cpp/pointers-cpp.md)