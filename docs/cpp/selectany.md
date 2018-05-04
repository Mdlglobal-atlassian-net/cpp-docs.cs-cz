---
title: selectany | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- selectany_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6543188525bea9a04c82bf5202160b42bcb6b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="selectany"></a>selectany
**Konkrétní Microsoft**  
  
 Říká kompilátoru, že deklarovaná položka globálních dat (proměnná nebo objekt) je vybrána libovolnou sekvencí COMDAT (zabalenou funkcí).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec( selectany ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je v době spojení nalezeno více definic sekvencí COMDAT, linker jednu vybere a zbytek zahodí. Pokud – možnost linkeru [/OPT:REF](../build/reference/opt-optimizations.md) (optimalizace) je vybraná, pak sekvence COMDAT odstranění dojde k odebrání všech neregistrované datové položky ve výstupu linkeru.  
  
 Konstruktory a přiřazení pomocí globálních funkcí nebo statických metod v deklaraci nevytvoří odkaz a nezabrání eliminaci možnosti /OPT:REF. Vedlejší účinky takového kódu by neměly být závislé na tom, zda neexistují žádné odkazy na tato data.  
  
 U dynamicky inicializovaných globálních objektů zahodí atribut `selectany` také kód inicializace objektu bez odkazu.  
  
 V projektu EXE nebo DLL lze položku globálních dat obvykle inicializovat pouze jednou. Atribut `selectany` lze použít při inicializaci globálních dat definovaných hlavičkami, když se stejná hlavička objeví ve více než jednom zdrojovém souboru. Atribut `selectany` je k dispozici v kompilátorech jazyka C i jazyka C++.  
  
> [!NOTE]
>  Atribut `selectany` lze použít pouze pro vlastní inicializaci položek globálních dat, které jsou externě viditelné.  
  
## <a name="example"></a>Příklad  
 Tento kód ukazuje, jak použít atribut `selectany`:  
  
```  
//Correct - x1 is initialized and externally visible   
__declspec(selectany) int x1=1;  
  
//Incorrect - const is by default static in C++, so   
//x2 is not visible externally (This is OK in C, since  
//const is not by default static in C)  
const __declspec(selectany) int x2 =2;  
  
//Correct - x3 is extern const, so externally visible  
extern const __declspec(selectany) int x3=3;  
  
//Correct - x4 is extern const, so it is externally visible  
extern const int x4;  
const __declspec(selectany) int x4=4;  
  
//Incorrect - __declspec(selectany) is applied to the uninitialized  
//declaration of x5  
extern __declspec(selectany) int x5;  
  
// OK: dynamic initialization of global object  
class X {  
public:  
X(int i){i++;};  
int i;  
};  
  
__declspec(selectany) X x(1);  
```  
  
## <a name="example"></a>Příklad  
 Tento kód ukazuje způsob použití `selectany` atribut zajistit data sekvence COMDAT skládání, pokud používáte [/OPT:ICF](../build/reference/opt-optimizations.md) – možnost linkeru. Všimněte si, že data musí být označen `selectany` a umístěný v **const** část (jen pro čtení). Část jen pro čtení je nutné explicitně zadat.  
  
```  
// selectany2.cpp  
// in the following lines, const marks the variables as read only  
__declspec(selectany) extern const int ix = 5;  
__declspec(selectany) extern const int jx = 5;  
int main() {  
   int ij;  
   ij = ix + jx;  
}  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)