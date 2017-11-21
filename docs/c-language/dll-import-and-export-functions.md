---
title: "Knihovny DLL Import a Export funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78d1dacd764a7d171c9cacb54a64fab241f8603a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dll-import-and-export-functions"></a>Import a export funkcí knihovny DLL
**Konkrétní Microsoft**  
  
 Nejvíce dokončení a aktuální informace o tomto tématu najdete v [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 **Dllimport** a `dllexport` modifikátory třídy úložiště jsou specifické pro společnost Microsoft rozšíření pro jazyk C. Tyto modifikátory explicitně definují rozhraní DLL svému klientu (spustitelnému souboru nebo jiné knihovně DLL). Deklarace funkcí s modifikátorem `dllexport` odstraňuje potřebu souboru definice modulu (.DEF). Můžete také **dllimport** a `dllexport` modifikátory s daty a objekty.  
  
 **Dllimport** a `dllexport` modifikátory třídy úložiště musí být použit s – klíčové slovo rozšířených atributů syntaxe `__declspec`, jak je uvedeno v následujícím příkladu:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllExport int j;  
DllExport int n;  
```  
  
 Konkrétní informace o syntaxi pro modifikátory rozšířené třídy úložiště najdete v tématu [rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Definice funkcí jazyka C](../c-language/c-function-definitions.md)