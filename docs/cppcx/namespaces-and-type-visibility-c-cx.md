---
title: "Obory názvů a viditelnost typů (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
caps.latest.revision: "13"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 09d0000dd7ac6fbe7c57d0b903694754e2d390e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Obory názvů a viditelnost typů (C + +/ CX)
Obor názvů je standardní C++ konstrukce pro typy, které mají související s funkcí seskupování a brání kolize názvů v knihovnách. Systém typů prostředí Windows Runtime vyžaduje, aby všechny veřejné typy prostředí Windows Runtime, včetně těch, které v kódu, musí být deklarován v oboru názvů v oboru názvů. Veřejné typy, které jsou deklarované v globálním oboru nebo vnořit do jiné třídy, způsobí chybu kompilace.  
  
 Soubor .winmd musí mít stejný název, který má kořenového oboru názvů. Například třídu, která je s názvem A.B.C.MyClass se dá vytvořit instance pouze v případě, že je definována v souboru metadat, který je pojmenován A.winmd nebo A.B.winmd nebo A.B.C.winmd. Název spustitelného souboru nemusí odpovídat názvu souboru .winmd.  
  
## <a name="type-visibility"></a>Viditelnost typů  
 V oboru názvů, typy prostředí Windows Runtime – na rozdíl od standardní typy C++ – mít privátní nebo veřejné usnadnění. Ve výchozím nastavení je usnadnění soukromé. Pouze veřejné typ je viditelná pro metadata a je proto použití z aplikací a součástí, které může být napsán v jiných jazyků než C++. Pravidla pro viditelné typy jsou obecně více omezující než pravidla pro typy neviditelné, protože viditelné typy nelze vystavit C++ konkrétní koncepty, které nejsou podporované v jazyce .NET nebo JavaScript.  
  
> [!NOTE]
>  Metadata obsazením pouze v době běhu jazyky rozhraní .NET a JavaScript. Když je C++ aplikace nebo součást rozhovoru s jinou C++ aplikace nebo součást – to zahrnuje součásti systému Windows, které jsou napsané v jazyce C++ – pak bez běhové spotřeby metadat se vyžaduje.  
  
## <a name="member-accessibility-and-visibility"></a>Člen usnadnění a viditelnost  
 Ve třídě privátní ref, rozhraní nebo delegáta jsou vygenerované žádní členové k metadatům, i v případě, že mají veřejnou dostupnost. Ve veřejné ref třídách můžete řídit viditelnost členů v metadatech nezávisle na jejich usnadnění ve zdrojovém kódu. Stejně jako standardní C++ použít Princip nejnižších nutných oprávnění; Nevytvářejte členové vaší viditelné v metadatech Pokud nezbytně musí být.  
  
 Použijte následující modifikátory přístupu k řízení viditelnost metadat a usnadnění zdrojového kódu.  
  
||||  
|-|-|-|  
|Modifikátor|Význam|Vygenerované k metadatům?|  
|private|Výchozí usnadnění. Stejný význam jako standardní C++.|Ne|  
|protected|Stejný význam jako standardní C++, jak v rámci aplikace nebo součásti i v metadatech.|Ano|  
|public|Stejný význam jako standardní C++.|Ano|  
|`public protected`- nebo -`protected public`|Chráněný usnadnění v metadatech, veřejné v rámci aplikace nebo součást.|Ano|  
|`protected private`nebo`private protected`|Nejsou viditelné v metadatech; usnadnění přístupu v rámci aplikace nebo součást chráněný.||  
|`internal`nebo`private public`|Člen je veřejný v rámci aplikace nebo součásti, ale není viditelná v metadatech.|Ne|  
  
## <a name="windows-runtime-namespaces"></a>Obory názvů prostředí Windows Runtime  
 Rozhraní API systému Windows se skládá z typů, které jsou deklarované v systému Windows::\* obory názvů. Tyto obory názvů jsou vyhrazené pro Windows a typy nelze přidat k nim. V **Prohlížeč objektů**, zobrazí se tyto obory názvů v souboru windows.winmd. Dokumentaci o těchto oborech názvů najdete v tématu [rozhraní API systému Windows](http://msdn.microsoft.com/library/windows/apps/br211377).  
  
## <a name="ccx-namespaces"></a>C + +/ CX obory názvů  
 C + +/ CX definovat určité typy v tyto obory názvů v rámci projekce systém typů prostředí Windows Runtime.  
  
|||  
|-|-|  
|**Namespace**|**Popis**|  
|default|Obsahuje vestavěné typy číselné a char16. Tyto typy jsou v oboru v každé oboru názvů a `using` příkaz vyžádáním nikdy.|  
|Platforma|Obsahuje primárně veřejné typy, které odpovídají typům prostředí Windows Runtime, jako `Array<T>`, `String`, `Guid`, a `Boolean`. Také zahrnuje typy specializované pomocné rutiny, jako `Platform::Agile<T>` a `Platform::Box<T>`.|  
|Platform::Collections|Obsahuje třídy konkrétní kolekce, které implementují rozhraní pro kolekce prostředí Windows Runtime `IVector`, `IMap`a tak dále. Tyto typy jsou definovány v záhlaví souboru collection.h, není v platform.winmd.|  
|Platform::details|Obsahuje typy, které se používají kompilátoru a nejsou určeny pro veřejné spotřeby.|  
  
## <a name="see-also"></a>Viz také  
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)