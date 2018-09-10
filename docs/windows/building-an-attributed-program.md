---
title: Sestavení programu s atributy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tlb files [C++]
- MIDL
- MIDL, linker output
- IDL files [C++]
- building type libraries and .idl files
- .tlb files [C++]
- .idl files [C++]
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2fc148478433106eabdb2bc57ef7bb6c91d13601
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315286"
---
# <a name="building-an-attributed-program"></a>Sestavení programu s atributy

Poté, co vložíte do zdrojového kódu jazyka Visual C++ atributy, můžete kompilátor Visual C++ k vytvoření souboru typu knihovna a .idl za vás. Následující linkeru možnosti tvorbu souborů .tlb a IDL:

- [/ IDLOUT](../build/reference/idlout-name-midl-output-files.md)

- [/ IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)

- [/ TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)

Některé projekty obsahují více souborů .idl nezávislé. Slouží k vytvoření dvou nebo více souborů .tlb a svázat ho Volitelně můžete do bloku prostředků. Tento scénář není aktuálně podporován v jazyce Visual C++.

Kromě toho výstup linkeru jazyka Visual C++ všechny informace o atributu souvisejícím s IDL do jednoho souboru MIDL. Nebude žádný způsob, jak generovat dvě knihovny typů z jednoho projektu.

## <a name="see-also"></a>Viz také

[Koncepty](../windows/attributed-programming-concepts.md)