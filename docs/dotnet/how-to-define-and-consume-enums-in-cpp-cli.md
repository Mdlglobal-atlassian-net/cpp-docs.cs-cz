---
title: "Postupy: definice a používání výčtů v jazyce C + +/ CLI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f4243400f20ae30fe1a2bc3826f052eb534297b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Postupy: Definice a používání výčtů v jazyce C++/CLI
Toto téma popisuje výčty v jazyce C + +/ CLI.  
  
## <a name="specifying-the-underlying-type-of-an-enum"></a>Určení podkladový typ výčtového  
 Ve výchozím nastavení, je základní typ výčtu `int`.  Můžete však zadat typ, který má být podepsaný držitelem nebo bez znaménka formy `int`, `short`, `long`, `__int32`, nebo `__int64`.  Můžete také použít `char`.  
  
```  
// mcppv2_enum_3.cpp  
// compile with: /clr  
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};  
  
int main() {  
   // fully qualified names, enumerator not injected into scope  
   day_char d = day_char::sun, e = day_char::mon;  
   System::Console::WriteLine(d);  
   char f = (char)d;  
   System::Console::WriteLine(f);  
   f = (char)e;  
   System::Console::WriteLine(f);  
   e = day_char::tue;  
   f = (char)e;  
   System::Console::WriteLine(f);  
}  
```  
  
 **Výstup**  
  
```Output  
sun  
0  
1  
2  
```  
  
## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Postup převedení mezi spravovanými a standardními výčty  
 Neexistuje žádný standardní převod mezi výčet a typ integrální; přetypování je povinný.  
  
```  
// mcppv2_enum_4.cpp  
// compile with: /clr  
enum class day {sun, mon, tue, wed, thu, fri, sat};  
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum  
  
int main() {  
   day a = day::sun;  
   day2 = sun;  
   if ((int)a == day2)  
   // or...  
   // if (a == (day)day2)  
      System::Console::WriteLine("a and day2 are the same");  
   else  
      System::Console::WriteLine("a and day2 are not the same");  
}  
```  
  
 **Výstup**  
  
```Output  
a and day2 are the same  
```  
  
## <a name="operators-and-enums"></a>Operátory a výčty  
 Následující operátory jsou platné ve výčty v jazyce C + +/ CLI:  
  
|Operátor|  
|--------------|  
|== != \< > \<= >=|  
|+ -|  
|&#124; ^ & ~|  
|++ --|  
|sizeof|  
  
 Operátory &#124; ^ & ~ ++ – jsou definovány pouze pro výčty s integrální základní typy, není včetně bool.  Oba operandy musí být výčtového typu.  
  
 Kompilátor nemá žádné statickou nebo dynamickou kontrola výsledku operace výčtu; Výsledkem operace může být hodnota není v rozsahu je výčet platný výčty.  
  
> [!NOTE]
>  C ++ 11 zavádí výčtu typy tříd v nespravovaném kódu, které se významně liší od spravovaných výčet tříd v jazyce C + +/ CLI. Na konkrétní typ třídy C ++ 11 výčtu nepodporuje stejné operátory jako typ výčtu spravované třídy v jazyce C + +/ CLI a C + +/ CLI zdrojový kód musíte zadat usnadnění specifikace v spravované výčtu deklarace tříd aby bylo možné odlišit od nespravované (C++ 11) deklarace tříd výčtu. Další informace o výčet tříd v jazyce C + +/ CLI, C + +/ CX a C ++ 11, najdete v části [výčet tříd](../windows/enum-class-cpp-component-extensions.md).  
  
```  
// mcppv2_enum_5.cpp  
// compile with: /clr  
private enum class E { a, b } e, mask;  
int main() {  
   if ( e & mask )   // C2451 no E->bool conversion  
      ;  
  
   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)  
      ;  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```  
  
```  
// mcppv2_enum_6.cpp  
// compile with: /clr  
private enum class day : int {sun, mon};  
enum : bool {sun = true, mon = false} day2;  
  
int main() {  
   day a = day::sun, b = day::mon;  
   day2 = sun;  
  
   System::Console::WriteLine(sizeof(a));  
   System::Console::WriteLine(sizeof(day2));  
   a++;  
   System::Console::WriteLine(a == b);  
}  
```  
  
 **Výstup**  
  
```Output  
4  
1  
True  
```  
  
## <a name="see-also"></a>Viz také  
 [enum – třída](../windows/enum-class-cpp-component-extensions.md)