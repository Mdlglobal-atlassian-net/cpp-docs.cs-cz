---
title: "Upozornění sestavení projektu PRJ0041 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0041
dev_langs: C++
helpviewer_keywords: PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e5a9d5fb5350e4ae6b33fc167aae14b1361291e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-warning-prj0041"></a>Upozornění sestavení projektu PRJ0041
Nelze najít chybějící závislost 'závislosti' souboru 'file'. Může stále sestavení projektu, ale může nadále vypadat zastaralý, dokud nebude nalezen tento soubor.  
  
 Soubor (zdrojový soubor nebo soubor.idl/.odl, například obsahovala příkazu zahrnout, který nebylo možné přeložit systému projektu.  
  
 Protože systém projektu nezpracovává preprocesoru příkazy (například #if), nemusí být příkaz problematické ve skutečnosti součástí sestavení.  
  
 Toto upozornění vyřešit, odstraňte všechny nepotřebné kód v soubory .rc nebo přidejte zástupné soubory odpovídající název.