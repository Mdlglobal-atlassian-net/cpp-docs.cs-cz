---
title: Ukazatelé const a volatile | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52550df1ca89ec1252fc2910bf27598d51302495
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212258"
---
# <a name="const-and-volatile-pointers"></a>Ukazatelé const a volatile
[Const](../cpp/const-cpp.md) a [volatile](../cpp/volatile-cpp.md) klíčová slova změnit způsob práce s ukazateli. **Const** – klíčové slovo určuje, že ukazatel myši se nemůže modifikovat po inicializaci; ukazatel je chráněn před úpravami.  
  
 **Volatile** – klíčové slovo určuje, že hodnotu přiřazenou k následujícímu názvu lze upravit akcemi i mimo aplikaci uživatele. Proto **volatile** – klíčové slovo je užitečné k deklaraci objektů ve sdílené paměti, který je přístupný několik procesů nebo oblastí globálních dat používaných pro komunikaci s rutinami služby přerušení.  
  
 Pokud je název deklarovaný jako **volatile**, kompilátor znovu načte hodnotu z paměti pokaždé, když je k nim přistupovat pomocí programu. Tím jsou výrazně omezeny možné optimalizace. Pokud však může dojít k nečekané změně stavu objektu, jde o jediný způsob, jak lze zajistit předvídatelný výkon programu.  
  
 Chcete-li deklarovat objekt, který ukazuje ukazatel, jako **const** nebo **volatile**, použijte deklaraci následujícího tvaru:  
  
```cpp 
const char *cpch;  
volatile char *vpch;  
```  
  
 Chcete-li deklarovat hodnotu ukazatele — tedy skutečnou adresu uloženou v ukazateli – jako **const** nebo **volatile**, použijte deklaraci následujícího tvaru:  
  
```cpp 
char * const pchc;  
char * volatile pchv;  
```  
  
 Jazyk C++ znemožňuje přiřazení, která by umožnila úpravu objektu nebo ukazatele deklarovaného jako **const**. Taková přiřazení by odstranila informaci, s níž byl objekt nebo ukazatel deklarován, a porušila by tak záměr původní deklarace. Vezměte v úvahu následující deklarace:  
  
```cpp 
const char cch = 'A';  
char ch = 'B';  
```  
  
 Dány předchozí deklarace dvou objektů (`cch`, typu **const char**, a `ch`, typu **char)**, jsou následující deklarace či inicializace platné:  
  
```cpp 
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 Následující deklarace či inicializace jsou chybné.  
  
```cpp 
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 Deklarace proměnné `pch2` deklaruje ukazatel, pomocí kterého lze upravit konstantní objekt, a proto není povolena. Deklarace `pch3` Určuje, že ukazatel myši je konstantní, nikoli objekt; deklarace není povolena ze stejného důvodu `pch2` deklarace není povolena.  
  
 Následujících osm přiřazení ukazuje přiřazování pomocí ukazatele a změnu hodnoty ukazatele z předchozích deklarací. Pro tuto chvíli předpokládejme, že pro proměnné `pch1` až `pch8` byla inicializace správná.  
  
```cpp 
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 Ukazatele deklarované jako **volatile**, nebo jako kombinaci **const** a **volatile**, dodržují stejná pravidla.  
  
 Ukazatele na **const** objekty se často používají v deklaracích funkcí následujícím způsobem:  
  
```cpp 
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 Předchozí příkaz deklaruje funkci [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), kde dva ze tří argumentů jsou typu ukazatele do **char**. Protože jsou argumenty jsou předány podle odkazu a podle hodnoty, funkce nebude měnit parametry `strDestination` a `strSource` Pokud `strSource` nebyl deklarován jako **const**. Deklarace `strSource` jako **const** volajícímu zajišťuje, že `strSource` nelze volanou funkcí změnit.  
  
> [!NOTE]
> Protože existuje standardní převod z *typename* <strong>\*</strong> k **const** *typename* <strong>\*</strong>, je platný pro předání argumentu typu `char *` k [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Ale opak není pravdou; Chcete-li odebrat neexistuje žádný implicitní převod **const** atribut z objektu nebo ukazatele.  
  
 A **const** ukazatel daného typu lze přiřadit ukazateli stejného typu. Ukazatel, který ale není **const** nelze přiřadit **const** ukazatele. Následující kód ukazuje správná i nesprávná přiřazení:  
  
```cpp 
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 Následující příklad ukazuje, jak deklarovat objekt jako const, pracujete-li s ukazatelem na ukazatel na objekt.  
  
```cpp 
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
  
## <a name="see-also"></a>Viz také:  
 [Ukazatele](../cpp/pointers-cpp.md)