---
title: Závažná chyba C1211 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef92816c157d6bbc72d7c7539f2d0644c70082b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199363"
---
# <a name="fatal-error-c1211"></a>Závažná chyba C1211
Vlastní atribut TypeForwardedTo nepodporuje verzi modulu runtime nainstalován  
  
 C1211 nastane, když máte kompilátoru pro aktuální verzi, ale CLR z předchozí verze.  
  
 Některé funkce kompilátoru nemusí fungovat na předchozí verzi čas spuštění.  
  
 Chcete-li vyřešit C1211 instalace modul common language runtime, která odeslaná s překladačem používáte.  
  
 Další informace najdete v tématu [předávání typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).