---
title: "Sestavení programu s atributy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3e39bbd2b630d35942c1c5107041b2fbadf7549
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="building-an-attributed-program"></a>Sestavení programu s atributy
Po přepnutí atributy Visual C++ do zdrojového kódu, můžete kompilátor Visual C++ k vytvoření typu knihovny a .idl souboru pro vás. Následující linkeru možnosti nápovědy sestavení .tlb a .idl souborů:  
  
-   [/ IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/ IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/ TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 Některé projekty obsahují několik nezávislých .idl souborů. Ty se používají vytvořit dva soubory .tlb a volitelně svázat ho do bloku prostředků. Tento scénář není podporován v jazyce Visual C++.  
  
 Kromě toho výstup linkeru jazyka Visual C++ všechny informace o atributu souvisejícím s IDL do jednoho souboru MIDL. Budou existovat žádný způsob, jak vygenerovat dvě knihovny typů z jednoho projektu.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../windows/attributed-programming-concepts.md)