---
title: "C2592 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2592
dev_langs: C++
helpviewer_keywords: C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5f6483a168ffe5f7b487932770226c834b7fd611
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2592"></a>C2592 chyby kompilátoru
'class': 'base_class_2' je zděděn z 'base_class_1' a nejde ho znovu zadaný  
  
 Zadávat lze pouze základní třídy, které nedědí z jiné základní třídy. V tomto případě pouze `base_class_1` je potřeba ve specifikaci `class` protože `base_class_1` již dědí `base_class_2`.