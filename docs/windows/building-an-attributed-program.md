---
title: Sestavení programu s atributy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d87f95b456e3f99598f48e6ffa8ad29806aa168
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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