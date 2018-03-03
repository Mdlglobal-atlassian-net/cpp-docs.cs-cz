---
title: Konfigurace Visual C++ pro procesory ARM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8539578e8030862e63f4dda36c6b9c93a29547ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="configure-visual-c-for-arm-processors"></a>Konfigurace Visual C++ pro procesory ARM

Tato část dokumentace obsahuje informace o tom, jak pomocí nástrojů Visual C++ sestavení cíle ARM hardwaru.  
  
## <a name="in-this-section"></a>V tomto oddílu  

[Přehled konvencí ARM ABI](../build/overview-of-arm-abi-conventions.md)  
Popisuje binární rozhraní aplikace, které se používá Windows on ARM pro využití registrů, konvence volání a výjimek.  
  
[Běžné problémy s migrací ARM v prostředí Visual C++](../build/common-visual-cpp-arm-migration-issues.md)  
Popisuje elementy kódu C++, které jsou běžně předpokládá, že přenosné v architekturách, ale který mít různé výsledky pro ARM než pro x86 a x64.  
  
[Zpracování výjimek ARM](../build/arm-exception-handling.md)  
Popisuje schéma kódování pro během strukturované zpracování výjimek v systému Windows na ARM unwinding zásobníku.  
  
## <a name="related-sections"></a>Související oddíly  
  
[ARM – vnitřní prvky](../intrinsics/arm-intrinsics.md)  
Popisuje překladač pro procesory, které používají architekturu ARM.