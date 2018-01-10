---
title: "Závažná chyba C1854 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1854
dev_langs: C++
helpviewer_keywords: C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e0a26e902b1a40203bb4323bce8e28e687e9647
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1854"></a>Závažná chyba C1854
  
> nelze přepsat informace vytvořen během vytváření předkompilovaných hlaviček v objektu souboru: "*filename*.  
  
Kterou jste zadali [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) možnost po zadání [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) možnost u stejného souboru.  
  
Chcete-li tento problém vyřešit, obecně platí, nastavte pouze jeden soubor ve vašem projektu a zkompilovat pomocí **/Yc** možnost a nastavte všechny ostatní soubory zkompilovat pomocí **/Yu** možnost. Podrobnosti o použití **/Yc** možnost a nastavte ji v integrovaném vývojovém prostředí sady Visual Studio naleznete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md). Další informace o použití předkompilovaných hlaviček najdete v tématu [vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md).  
