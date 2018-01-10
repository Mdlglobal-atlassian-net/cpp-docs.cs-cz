---
title: proces | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: process_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6754adcb348cb6eb061e32fc58e78f43663b1a90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="process"></a>zpracování
Určuje, že proces spravované aplikace by měl používat jednu kopii určité globální proměnné, statické členské proměnné nebo statické místní proměnné sdílené ve všech doménách aplikace v procesu. Tento způsob primárně určený pro použití při kompilaci s **/CLR: čistý**, protože v rámci **/CLR: pure** na doménu aplikace se ve výchozím nastavení jsou globální a statické proměnné. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015. Při kompilaci s **/CLR**, globální a statické proměnné jsou podle procesu, ve výchozím nastavení (není potřeba použít `__declspec(process)`.  
  
 Modifikátorem `__declspec(process)` může být označena pouze globální, statická členská nebo statická místní proměnná nativního typu.  
  
 Při kompilaci s **/CLR: pure**, proměnné označené podle procesu musí být také deklarována jako `const`. Tím je zajištěno, že se proměnné pro proces nezmění v jedné doméně aplikace a poskytnou neočekávané výsledky v jiné doméně aplikace. Primární zamýšlené použití `__declspec(process)` je umožnit kompilace čas inicializace – globální proměnná, statické členské proměnné nebo statické místní proměnné v části **/CLR: pure**.  
  
 `process`je platný pouze při kompilaci s [/CLR](../build/reference/clr-common-language-runtime-compilation.md) nebo **/CLR: pure** a není platný, když kompilujete s **/CLR: safe**.  
  
 Pokud chcete domén aplikace, které chcete mít svůj vlastní kopii globální proměnné, použijte [appdomain](../cpp/appdomain.md).  
  
 V tématu [domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)