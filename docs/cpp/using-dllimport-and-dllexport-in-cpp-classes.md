---
title: Používání příkazů dllimport a dllexport ve třídách jazyka C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c7768558b735644a8f98a9380a509098c62dfeb
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947720"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Používání příkazů dllimport a dllexport ve třídách jazyka C++
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Můžete deklarovat třídy jazyka C++ se **dllimport** nebo **dllexport** atribut. Tyto formy vyjadřuje, že je celá třída importovaná nebo exportovaná. Třídy exportované tímto způsobem se nazývají exportovatelné třídy.  
  
 Následující příklad definuje exportovatelné třídy. Jsou exportovány všechny členské funkce a statická data:  
  
```cpp 
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 Všimněte si, že explicitní použití atributu **dllimport** a **dllexport** atributy u členů exportovatelné třídy je zakázáno.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> Třídy dllexport  
 Pokud deklarujete třídu **dllexport**, jsou exportovány všechny členské funkce a statické datové členy. Musíte zadat definice všech těchto členů ve stejném programu. V opačném případě je generována chyba linkeru. Jedinou výjimkou tohoto pravidla platí pro čistě virtuální funkce, pro které nemusíte poskytnout explicitní definice. Ale protože destruktor abstraktní třídy je vždy volán destruktorem základní třídy, čistě virtuální destruktory musí vždy poskytnout definici. Všimněte si, že tato pravidla jsou stejné pro neexportovatelné třídy.  
  
 Pokud exportujete data typu třídy nebo funkce, které vracejí třídy, je nutné exportovat třídy.  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> Třídy DllImport  
 Pokud deklarujete třídu **dllimport**, jsou importovány všechny členské funkce a statické datové členy. Na rozdíl od chování **dllimport** a **dllexport** pro typy nonclass, statické datové členy nelze zadat definovat ve stejném programu, ve kterém **dllimport** je třída definice.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> Dědičnost a exportovatelné třídy  
 Všechny základní třídy exportovatelné třídy musí být exportovatelný. V opačném případě bude vyvoláno upozornění kompilátoru. Kromě toho všechny dostupné členy, které jsou také třídy musí být exportovatelný. Toto pravidlo povoluje **dllexport** třída dědí z **dllimport** třídy a **dllimport** dědit ze třídy **dllexport** třídy (i když se tento případ nedoporučuje). Zpravidla vše, co je přístupné pro klienta knihovny DLL (podle pravidel přístupu jazyka C++) by měla být součástí rozhraní. To zahrnuje privátní členy dat zmiňované ve vložených funkcích.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> Import a Export výběrových členů  
 Vzhledem k tomu, že členské funkce a statická data v rámci třídy mají implicitně externí propojení, můžete je deklarovat **dllimport** nebo **dllexport** atribut, pokud není exportována celá třída. Pokud je celá třída importovaná nebo exportovaná, explicitní deklarace členské funkce a data jako **dllimport** nebo **dllexport** je zakázaná. Pokud deklarujete statického datového člena v rámci definice třídy jako **dllexport**, definice musí být někde v rámci stejného programu (stejně jako u externího propojení nonclass).  
  
 Podobně je možné deklarovat členské funkce se **dllimport** nebo **dllexport** atributy. V takovém případě je nutné zadat **dllexport** definice někde ve stejném programu.  
  
 Je vhodné si uvědomit několik důležitých bodů týkajících selektivní členské import a export:  
  
-   Import a export výběrových členů je nejvhodnější pro poskytování verze exportované třídy rozhraní, které je více omezující; To znamená jeden pro kterou můžete navrhnout knihovnu DLL, která poskytuje méně veřejných a soukromých funkcí než jazyk by jinak neomezil. Je také vhodný pro optimalizaci exportovatelného rozhraní: Pokud víte, že je klient podle definice nelze získat přístup k některým osobním datům, není nutné exportovat celé třídy.  
  
-   Při exportu jedné virtuální funkce ve třídě, musíte exportovat všechny nebo poskytnout alespoň verze, které může klient použít přímo.  
  
-   Pokud máte třídu, ve které používáte selektivní členské import/export s virtuálními funkcemi, funkce musí být v rozhraní exportovatelné nebo definované jako inline (viditelné pro klienta).  
  
-   Pokud definujete člena jako **dllexport** , ale neobsahují v definici třídy, je vygenerována chyba kompilátoru. Musíte definovat člena v záhlaví třídy.  
  
-   I když definice členů třídy jako **dllimport** nebo **dllexport** je povolena, nemůžete přepsat rozhraní určené v definici třídy.  
  
-   Pokud definujete členskou funkci na místě, než je základní text definice třídy, ve kterém jste ji deklarovali, bude vyvoláno upozornění v případě, že funkce je definována jako **dllexport** nebo **dllimport** (Pokud je toto definice liší od uvedené v deklaraci třídy).  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)