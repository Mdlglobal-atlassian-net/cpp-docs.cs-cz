---
title: "Závažná chyba nástroje NMAKE U1045 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1045
dev_langs: C++
helpviewer_keywords: U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1820b33d59d7dd9b8c96c269dd65518bafb4f0d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1045"></a>Závažná chyba nástroje NMAKE U1045
spawn se nezdařilo: zpráva  
  
 Programu nebo příkaz volá NMAKE se nezdařila z důvodu dané. Když NMAKE volá jiný program – například kompilátoru nebo linkeru – volání může selhat nebo chybu, mohou být vráceny volané programem. Tato zpráva se používá chybové zprávě.  
  
 Chcete-li tento problém vyřešit, nejprve určete příčinu chyby. Můžete použít příkazy hlášené NMAKE [/n](../../build/nmake-options.md) možnost, chcete-li ověřit nastavení prostředí a opakujte akci, kterou provádí NMAKE na příkazovém řádku.