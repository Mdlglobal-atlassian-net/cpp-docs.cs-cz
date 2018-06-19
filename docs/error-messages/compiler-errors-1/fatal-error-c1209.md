---
title: Závažná chyba C1209 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1209
dev_langs:
- C++
helpviewer_keywords:
- C1209
ms.assetid: aa9ee10f-abe3-4683-9792-adca4cbbabb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bce9ebf0281981264c3abeb1485cdffb89410e68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227890"
---
# <a name="fatal-error-c1209"></a>Závažná chyba C1209
Přátelská sestavení nepodporuje verzi modulu runtime nainstalován  
  
 C1208 nastane, když máte kompilátoru pro aktuální verzi, ale CLR z předchozí verze.  
  
 Některé funkce kompilátoru nemusí fungovat na předchozí verzi čas spuštění.  
  
 Vyřešit C1209, nainstalujte modul common language runtime, který se dodává s kompilátoru, který používáte.  
  
 Další informace najdete v tématu [přátelských sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).