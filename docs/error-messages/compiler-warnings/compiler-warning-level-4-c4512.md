---
title: "Kompilátoru (úroveň 4) upozornění C4512 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4512
dev_langs:
- C++
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd2e50f97cfc0242e1ac4af93f2d6609ff4b59cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4512"></a>C4512 kompilátoru upozornění (úroveň 4)
'class': Nepodařilo se vygenerovat operátor přiřazení  
  
 Kompilátor nemůže generovat operátor přiřazení pro danou třídu. Nebyl vytvořen žádný operátor přiřazení.  
  
 Operátor přiřazení pro základní třídu, která není dostupný v odvozené třídě může způsobit toto upozornění.  
  
 Abyste se vyhnuli toto upozornění, zadejte operátor přiřazení uživatelem definované pro třídu.  
  
 Kompilátor bude také generovat funkce operátor přiřazení pro třídu, která nedefinuje jeden. Tento operátor přiřazení je memberwise kopii dat členům v objektu. Protože `const` datové položky nelze změnit po inicializaci, pokud obsahuje třídy `const` operátor přiřazení výchozí položky, nebude fungovat. Další příčinou C4512 upozornění je deklaraci nestatické datového členu odkazového typu. Pokud je vytvoření-kopírovatelná typu, je nutné také zabránit vytvoření kopie výchozí konstruktor.  
  
 Abyste mohli vyřešit upozornění C4512 kódu v jednom ze tří způsobů:  
  
-   Operátor přiřazení pro třídu explicitně definujte.  
  
-   Odebrat **const** nebo operátor odkaz z položky dat ve třídě.  
  
-   Použít #pragma [upozornění](../../preprocessor/warning.md) příkaz k potlačení upozornění.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4512.  
  
```  
// C4512.cpp  
// compile with: /EHsc /W4  
// processor: x86  
  
class Base {  
private:  
   const int a;  
  
public:  
   Base(int val = 0) : a(val) {}  
   int get_a() { return a; }  
};   // C4512 warning  
  
class Base2 {  
private:  
   const int a;  
  
public:  
   Base2(int val = 0) : a(val) {}  
   Base2 & operator=( const Base2 & ) { return *this; }  
   int get_a() { return a; }  
};  
  
// Type designer intends this to be non-copyable because it has a   
// reference member  
class Base3  
{  
private:  
   char& cr;  
  
public:  
   Base3(char& r) : cr(r) {}  
   // Uncomment the following line to explicitly disable copying:  
   // Base3(const Base3&) = delete;   
};   // C4512 warning  
  
int main() {  
   Base first;  
   Base second;  
  
   // OK  
   Base2 first2;  
   Base2 second2;  
  
   char c = 'x';  
   Base3 first3(c);  
   Base3 second3 = first3; // C2280 if no default copy ctor  
}  
```