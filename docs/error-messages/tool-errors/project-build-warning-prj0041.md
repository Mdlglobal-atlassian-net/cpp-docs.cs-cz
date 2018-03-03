---
title: "Upozornění sestavení projektu PRJ0041 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 231b58cb0c13d1a3f87e010a5100da564b0be806
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0041"></a>Upozornění sestavení projektu PRJ0041
Nelze najít chybějící závislost 'závislosti' souboru 'file'. Může stále sestavení projektu, ale může nadále vypadat zastaralý, dokud nebude nalezen tento soubor.  
  
 Soubor (zdrojový soubor nebo soubor.idl/.odl, například obsahovala příkazu zahrnout, který nebylo možné přeložit systému projektu.  
  
 Protože systém projektu nezpracovává preprocesoru příkazy (například #if), nemusí být příkaz problematické ve skutečnosti součástí sestavení.  
  
 Toto upozornění vyřešit, odstraňte všechny nepotřebné kód v soubory .rc nebo přidejte zástupné soubory odpovídající název.