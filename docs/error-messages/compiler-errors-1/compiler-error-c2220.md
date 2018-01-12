---
title: "C2220 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2220
dev_langs: C++
helpviewer_keywords: C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 14da9ea0905f2aa7aa67c2b7524314a4af74246b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2220"></a>C2220 chyby kompilátoru
upozornění vyhodnocena jako chyba - žádný objekt souboru vygenerovaného  
  
 [/WX](../../build/reference/compiler-option-warning-level.md) určuje kompilátor zpracovává všechna upozornění jako chyby. Vzhledem k tomu, že došlo k chybě, nebyl vygenerován žádný objekt nebo spustitelný soubor.  
  
 Tato chyba se zobrazí, pouze když **wdn** je nastavený příznak a upozornění dojde během kompilace. Pokud chcete vyřešit tuto chybu, musí eliminovat každých upozornění ve vašem projektu.  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>Pokud chcete vyřešit, použijte jednu z následujících postupů  
  
-   Opravte problémy, které způsobí upozornění ve vašem projektu.  
  
-   Kompilace na nižší úrovni upozornění – například použít **/W3** místo **/W4**.  
  
-   Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma zakázat nebo konkrétní upozornění potlačit.  
  
-   Nepoužívejte **wdn** zkompilovat.