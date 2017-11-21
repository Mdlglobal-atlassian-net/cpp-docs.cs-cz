---
title: "Závažná chyba C1352 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1352
dev_langs: C++
helpviewer_keywords: C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71f2bf8ef42896447d48c9cb3581006c2e3d7620
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1352"></a>Závažná chyba C1352
Neplatný nebo poškozený MSIL ve funkci 'function' z modulu 'file'  
  
 .netmodule byl předán pro kompilátor, ale kompilátor zjistil poškození v souboru.  Požádejte uživatele, který vytváří .netmodule prozkoumat.  
  
 Kompilátor nekontroluje .netmodule soubory pro všechny typy poškození.  Nicméně, zkontrolujte, zda všechny cesty ovládacího prvku ve funkci obsahovat příkaz return.  
  
 Další informace najdete v tématu [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).