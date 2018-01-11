---
title: "Slice – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
dev_langs: C++
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c49abb87a3a1b9c480c9267f21f6fc9d3de55b9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="slice-class"></a>slice – třída
Třída nástrojů k valarray –, který se používá k definování jednorozměrné podmnožiny valarray – nadřazené. Pokud valarray – považuje za dvourozměrná matice se všechny elementy ve pole, řez extrahuje vektoru v jednu dimenzi mimo dvourozměrná pole.  
  
## <a name="remarks"></a>Poznámky  
 Třída ukládá parametry, které charakterizovat objekt typu [slice_array](../standard-library/slice-array-class.md) podmnožinu valarray – je nepřímo vytvořený, když objekt třídy řez se zobrazí jako argument pro objekt třídy [valarray – ](../standard-library/valarray-class.md#op_at)  **\<Typ >**. Uložené hodnoty, které zadejte do něj podmnožinu vybraný z nadřazené valarray – patří:  
  
-   Počáteční index v valarray –.  
  
-   Celková délka, nebo počet elementů v řez.  
  
-   Stride, nebo vzdálenost mezi následné indexy elementů v valarray –.  
  
 Pokud sada definované řez je podmnožinou konstantní valarray –, řez je nové valarray –. Pokud sada definované řez je podmnožinou nonconstant valarray –, řez má sémantiku původní valarray – referenční dokumentace. Vyhodnocení mechanismus pro nonconstant valarray – třídy šetří čas a paměti.  
  
 Operace na valarray – třídy jsou zaručit pouze v případě, že zdrojový a cílový podmnožiny definované řezy jsou jedinečné a jsou platné všechny indexy.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[řez](#slice)|Definuje podmnožinu `valarray` který se skládá z řady elementy, které jsou do stejné vzdálenosti a která začínají zadaný element.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[velikost](#size)|Nalezne počet elementů v řez z `valarray`.|  
|[spuštění](#start)|Vyhledá počáteční index řezy `valarray`.|  
|[STRIDE](#stride)|Najde rozdíl mezi elementy v řez systému `valarray`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<valarray – >  
  
 **Namespace:** – std  
  
##  <a name="size"></a>Slice::size  
 Vyhledá v řez valarray – počet elementů.  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v řez valarray –.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// slice_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t sizeVA, sizeVAR;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i += 1 )  
      va [ i ] =  i+1;  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sizeVA = va.size ( );  
   cout << "The size of the valarray is: "  
        << sizeVA << "." << endl << endl;  
  
   slice vaSlice ( 3 , 6 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "The slice of valarray va is vaResult = "  
        << "va[slice( 3, 6, 3)] =\n ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   sizeVAR = vaSlice.size ( );  
   cout << "The size of slice vaSlice is: "  
        << sizeVAR << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).  
The size of the valarray is: 20.  
  
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =  
 ( 4 7 10 13 16 19 ).  
The size of slice vaSlice is: 6.  
```  
  
##  <a name="slice"></a>Slice::Slice  
 Definuje podmnožinu valarray –, která se skládá z prvky, které jsou do stejné vzdálenosti a která začínají zadaný element.  
  
```  
slice();

slice(
    size_t _StartIndex,  
    size_t _Len,   
    size_t stride);
```  
  
### <a name="parameters"></a>Parametry  
 `_StartIndex`  
 Valarray – index první prvek v podmnožině.  
  
 `_Len`  
 Počet elementů v podmnožině.  
  
 `stride`  
 Vzdálenost mezi elementy v podmnožině.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí konstruktor ukládá nulami pro počáteční index, celková délka a stride. Druhý konstruktor úložiště `_StartIndex` pro počáteční index, `_Len` pro celková délka a `stride` pro stride.  
  
### <a name="remarks"></a>Poznámky  
 Stride může mít zápornou hodnotu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// slice_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i+=1 )  
      va [ i ] =  2 * (i + 1 );  
  
   cout << "The operand valarray va is:\n( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   slice vaSlice ( 1 , 7 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "\nThe slice of valarray va is vaResult:"  
        << "\nva[slice( 1, 7, 3)] = ( ";  
      for ( i = 0 ; i < 7 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).  
  
The slice of valarray va is vaResult:  
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).  
```  
  
##  <a name="start"></a>Slice::Start  
 Vyhledá počáteční index řez valarray –.  
  
```  
size_t start() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počáteční index řez valarray –.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// slice_start.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t startVAR;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i += 1 )  
      va [ i ] = i+1;  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   slice vaSlice ( 3 , 6 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "The slice of valarray va is vaResult = "  
        << "va[slice( 3, 6, 3)] =\n ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   startVAR = vaSlice.start ( );  
   cout << "The start index of slice vaSlice is: "  
        << startVAR << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).  
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =  
 ( 4 7 10 13 16 19 ).  
The start index of slice vaSlice is: 3.  
```  
  
##  <a name="stride"></a>Slice::STRIDE  
 Najde rozdíl mezi elementy v řez valarray –.  
  
```  
size_t stride() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vzdálenost mezi elementy v řez valarray –.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// slice_stride.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t strideVAR;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i += 1 )  
      va [ i ] =  3 * ( i + 1 );  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   slice vaSlice ( 4 , 5 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "The slice of valarray va is vaResult = "  
        << "va[slice( 4, 5, 3)] =\n ( ";  
      for ( i = 0 ; i < 5 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   strideVAR = vaSlice.stride ( );  
   cout << "The stride of slice vaSlice is: "  
        << strideVAR << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).  
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =  
 ( 15 24 33 42 51 ).  
The stride of slice vaSlice is: 3.  
```  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

