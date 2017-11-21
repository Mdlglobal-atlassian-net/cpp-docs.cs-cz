---
title: "C2919 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2919
dev_langs: C++
helpviewer_keywords: C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a70b679d4add5fa4ad2904e3c0d103e1c8881280
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2919"></a>C2919 chyby kompilátoru
'type': operátory nelze použít na povrchu publikované WinRT typu  
  
 Systém typů prostředí Windows Runtime nepodporuje operátor členské funkce v publikované prostor typu. Je to proto, že ne všechny jazyky spotřebovat operátor členské funkce. Můžete vytvořit privátní nebo interní operátor členské funkce, které lze volat z kódu C++ ve stejné třídě nebo kompilace jednotce.  
  
 Chcete-li tento problém vyřešit, odeberte – členská funkce operátor z veřejné rozhraní nebo změňte jej na pojmenované členské funkce. Například místo z `operator==`, název členské funkce `Equals`.