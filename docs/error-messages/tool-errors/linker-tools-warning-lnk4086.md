---
title: "Upozornění linkerů Lnk4086 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4086
dev_langs: C++
helpviewer_keywords: LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 85965c09bdbdff3ec271d2e1c5ef1913650009c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4086"></a>Upozornění linkerů LNK4086
vstupní bod funkce není __stdcall s bajtů "číslo" argumentů; bitová kopie nemusí fungovat.  
  
 Vstupní bod pro knihovny DLL musí být `__stdcall`. Buď znovu zkompiluje funkce se [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) možnost nebo zadejte `__stdcall` nebo rozhraní WINAPI při definici funkce.