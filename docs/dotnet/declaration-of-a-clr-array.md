---
title: Deklarace pole CLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8d8b2a5d348887d56a1221a5a9125449e5356b9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="declaration-of-a-clr-array"></a>Deklarace pole CLR
Syntaxe pro deklarování, vytváření instancí a inicializace spravovaného pole změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Deklarace pole objektu CLR ve spravovaných rozšíření byla přípona deklarace standardní pole, ve kterém `__gc` mezi název objektu pole a jeho pravděpodobně dimenze určené čárkami, stejně jako následující dvojice byl umístěn – klíčové slovo Příklady:  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 To je jednodušší v nové syntaxi, ve které použijeme deklaraci jako šablona podobně jako standardní knihovna C++ `vector` deklarace. První parametr určuje typ elementu. Druhý parametr určuje rozměry pole (s výchozí hodnotou 1, takže jenom více dimenzí vyžadují druhý argument). Samotný objekt pole je sledovací popisovač a proto je třeba věnovat hat. Pokud typ elementu je také typu odkazu, taky vyžaduje hat. Například výše uvedený příklad při v nové syntaxe vypadá takto:  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 Protože typu odkazu je sledovací popisovač spíše než objekt, je možné určit pole CLR jako návratový typ funkce. (Na rozdíl od, není možné určit nativní pole jako návratový typ funkce.) Syntaxe pro to ve spravovaných rozšíření byla intuitivní. Příklad:  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 V jazyce Visual C++ prohlášení je mnohem jednodušší. Například  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 Zjednodušená inicializace místního spravovaného pole je podporována v obou verzích jazyka. Příklad:  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 je značně zjednodušené nové syntaxe (Všimněte si, že zabalení je implicitní v nové syntaxe `__box` operátor se odstranilo – viz [typy hodnot a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) diskusi):  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 Protože pole je odkaz na typ CLR, deklarace objektu každé pole je sledovací popisovač. Proto musí být pole objektů přiděleny na haldě CLR. (Zjednodušený zápis skryje přidělení spravovaná halda.) Zde je explicitní formu inicializace objektu pole v rámci spravovaného rozšíření:  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 V části nové syntaxe `new` výraz se nahradí `gcnew`. Velikosti dimenze jsou předány jako parametry, které `gcnew` výraz následujícím způsobem:  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 V nové syntaxe, můžete postupovat podle explicitní inicializační seznam `gcnew` výrazu; to není podporováno ve spravovaných rozšíření. Příklad:  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Pole](../windows/arrays-cpp-component-extensions.md)