---
title: "delete – operátor (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: delete_cpp
dev_langs: C++
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36da346329341221d43af2ec96aa17be4f819bf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="delete-operator-c"></a>delete – operátor (C++)
Zruší přidělení bloku paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 *Výraz cast* argument musí být ukazatel na blok dříve přidělené paměti pro objekt vytvořené pomocí [operátor new](../cpp/new-operator-cpp.md). **Odstranit** výsledek typu obsahuje operátor `void` a proto nevrací hodnotu. Příklad:  
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 Pomocí **odstranit** na ukazatel na objekt není přiřazen **nové** dává vést k neočekávaným výsledkům. Můžete však použít **odstranit** na ukazatel s hodnotou 0. Toto ustanovení znamená, že, když **nové** vrátí hodnotu 0 při selhání, odstraňování výsledek nezdařené **nové** operace je neškodné. V tématu [nové a odstraňte operátory](../cpp/new-and-delete-operators.md) Další informace.  
  
 **Nové** a **odstranit** operátory lze použít také pro vestavěné typy, včetně polí. Pokud `pointer` odkazuje na pole, je třeba před `pointer` umístit prázdné závorky:  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 Pomocí **odstranit** operátor objektu zruší přidělení jeho paměť. Program, který přistoupí přes ukazatel po odstranění objektu, může mít nepředvídatelné výsledky nebo se zhroutit.  
  
 Když **odstranit** se používá k navrácení paměti pro objekt třídy C++, destruktoru objektu je volána, než zrušení přidělení paměti objektu (Pokud objekt má destruktor).  
  
 Pokud operand pro **odstranit** operátor je upravitelnými l hodnota, jeho hodnota není definován po odstranění objektu.  
  
## <a name="using-delete"></a>Používání příkazu delete  
 Existují dvě varianty syntaxi pro [delete – operátor](../cpp/delete-operator-cpp.md): jeden pro jednotlivé objekty a druhou pro pole objektů. Následující fragment kódu ukazuje, jak se liší:  
  
```  
// expre_Using_delete.cpp  
struct UDType   
{  
};  
  
int main()  
{  
   // Allocate a user-defined object, UDObject, and an object  
   //  of type double on the free store using the  
   //  new operator.  
   UDType *UDObject = new UDType;  
   double *dObject = new double;  
   // Delete the two objects.  
   delete UDObject;  
   delete dObject;   
   // Allocate an array of user-defined objects on the  
   // free store using the new operator.  
   UDType (*UDArr)[7] = new UDType[5][7];  
   // Use the array syntax to delete the array of objects.  
   delete [] UDArr;  
}  
```  
  
 Následující dva případy vytvoří nedefinované výsledky: použitím operátoru delete (delete [ ]), který má podobu pole, na objekt a použitím operátoru delete, který nemá podobu pole, na pole.  
  
## <a name="example"></a>Příklad  
 Příklady použití **odstranit**, najdete v části [operátor new](../cpp/new-operator-cpp.md).  
  
## <a name="how-delete-works"></a>Jak funguje výraz delete  
 Operátor delete volá funkci **delete – operátor**.  
  
 Pro objekty nejsou typu třídy ([třída](../cpp/class-cpp.md), [struktura](../cpp/struct-cpp.md), nebo [– typ union](../cpp/unions.md)), je vyvolána v globální delete – operátor. Začne-li výraz delete jednočlenným operátorem rozlišení rozsahu (::), název funkce navracení je pro objekty typu třídy řešen v globálním oboru. V opačném případě operátor delete vyvolá destruktor objektu před zrušením přidělení paměti (pokud není ukazatel null). Operátor delete lze definovat na základě každé třídy. Neexistuje-li pro zadanou třídu žádná taková definice, je vyvolán globální operátor delete. Je-li výraz delete používán k zrušení přidělení objektu třídy, jehož statický typ má virtuální destruktor, je funkce zrušení přidělení řešena prostřednictvím virtuálního konstruktoru dynamického typu objektu.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Operátory new a delete](../cpp/new-and-delete-operators.md)   
 
