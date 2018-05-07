---
title: Upozornění sestavení projektu PRJ0041 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e845967b0a7116d6edade98b571de5bc1bcd9a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-warning-prj0041"></a>Upozornění sestavení projektu PRJ0041
Nelze najít chybějící závislost 'závislosti' souboru 'file'. Může stále sestavení projektu, ale může nadále vypadat zastaralý, dokud nebude nalezen tento soubor.  
  
 Soubor (zdrojový soubor nebo soubor.idl/.odl, například obsahovala příkazu zahrnout, který nebylo možné přeložit systému projektu.  
  
 Protože systém projektu nezpracovává preprocesoru příkazy (například #if), nemusí být příkaz problematické ve skutečnosti součástí sestavení.  
  
 Toto upozornění vyřešit, odstraňte všechny nepotřebné kód v soubory .rc nebo přidejte zástupné soubory odpovídající název.