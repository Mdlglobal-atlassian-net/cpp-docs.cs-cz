---
title: "sizeof – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sizeof_cpp
dev_langs: C++
helpviewer_keywords: sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f6cb6e9755b1a9a02c87fa713a9774945856b461
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sizeof-operator"></a>sizeof – operátor
Vypočítá velikost jeho operand s ohledem na velikost typu `char`.  
  
> [!NOTE]
>  Informace o `sizeof ...` operátor, najdete v části [tři tečky a Variadické šablony](../cpp/ellipses-and-variadic-templates.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sizeof unary-expression  
sizeof  ( type-name )  
```  
  
## <a name="remarks"></a>Poznámky  
 Výsledkem `sizeof` operátor je typu `size_t`, typ integrální definované v souboru zahrnout STDDEF. H. Tento operátor umožňuje Vyhněte se zadání velikosti data závislá na počítače ve vašich aplikacích.  
  
 Operand pro `sizeof` může být jedna z následujících akcí:  
  
-   Název typu. Chcete-li použít `sizeof` s názvem typu, názvu musí být uzavřena v závorkách.  
  
-   Výraz. Při použití s výrazem, `sizeof` lze zadat s nebo bez závorek. Výraz, nebude hodnocen.  
  
 Když `sizeof` operátor se použije pro objekt typu `char`, bude vrácen 1. Když `sizeof` operátor se použije pro pole, bude vrácen celkový počet bajtů v tomto poli není velikost ukazatele reprezentována identifikátor pole. Pokud chcete získat velikost ukazatele reprezentována identifikátor pole, předejte ji jako parametr funkce, která používá `sizeof`. Příklad:  
  
## <a name="example"></a>Příklad  
  
```  
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 Když `sizeof` operátor se použije pro `class`, `struct`, nebo `union` typu, výsledkem je počet bajtů v objektu daného typu, plus žádné odsazení přidány do zarovnat členy na hranicích aplikace word. Výsledek nutně neodpovídá velikosti vypočítat přidáním požadavky na úložiště jednotlivých členů. [/Zp](../build/reference/zp-struct-member-alignment.md) – možnost kompilátoru a [pack](../preprocessor/pack.md) – Direktiva pragma ovlivnit zarovnání hranice pro členy.  
  
 `sizeof` Operátor nikdy vypočítá 0, i pro třídu prázdný.  
  
 `sizeof` Operátor nelze použít s operandy následující:  
  
-   Funkce. (Ale `sizeof` lze použít na ukazatele na funkce.)  
  
-   Chvíli pole.  
  
-   Nedefinovaná třídy.  
  
-   Typ `void`.  
  
-   Pole přidělí dynamicky.  
  
-   Externí pole.  
  
-   Neúplné typy.  
  
-   Názvy v závorkách neúplné typy.  
  
 Když `sizeof` operátor použijí na odkaz, výsledkem je stejný jako `sizeof` měl použilo odkaz sám na sebe.  
  
 Je-li posledním prvkem struktury pole bez velikosti, operátor `sizeof` vrátí velikost struktury bez tohoto pole.  
  
 `sizeof` Operátor se často používá k výpočtu počet prvků v poli vlastnosti autorefresh pomocí výrazu ve formátu:  
  
```  
sizeof array / sizeof array[0]  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)