---
title: "Závažná chyba nástroje NMAKE U1056 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1056
dev_langs: C++
helpviewer_keywords: U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d53bee02d5fe910598a87e5837678d69f03f9cf9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1056"></a>Závažná chyba nástroje NMAKE U1056
Nelze najít procesor příkazů  
  
 Procesor příkazů nebyla na v zadané cestě **COMSPEC** nebo **cesta** proměnné prostředí.  
  
 NMAKE používá COMMAND.COM nebo CMD. EXE jako procesor příkazů při provádění příkazů. Hledá procesor příkazů nejprve v cestě nastavit **COMSPEC**. Pokud **COMSPEC** neexistuje, hledání NMAKE adresáře zadaný v **CESTU**.