---
title: "Závažná chyba C1209 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1209
dev_langs: C++
helpviewer_keywords: C1209
ms.assetid: aa9ee10f-abe3-4683-9792-adca4cbbabb5
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7791f8f910935f9d368a1592d1def2a84d805933
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1209"></a>Závažná chyba C1209
Přátelská sestavení nepodporuje verzi modulu runtime nainstalován  
  
 C1208 nastane, když máte kompilátoru pro aktuální verzi, ale CLR z předchozí verze.  
  
 Některé funkce kompilátoru nemusí fungovat na předchozí verzi čas spuštění.  
  
 Vyřešit C1209, nainstalujte modul common language runtime, který se dodává s kompilátoru, který používáte.  
  
 Další informace najdete v tématu [přátelských sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).