---
title: C2220 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d23476de35e0af45b46a775683ba8673b4959346
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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