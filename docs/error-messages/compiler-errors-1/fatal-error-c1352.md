---
title: Závažná chyba C1352 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 524b0bf5d25953c5c38cbe0e23dc5c7d9f3cb7be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226816"
---
# <a name="fatal-error-c1352"></a>Závažná chyba C1352
Neplatný nebo poškozený MSIL ve funkci 'function' z modulu 'file'  
  
 .netmodule byl předán pro kompilátor, ale kompilátor zjistil poškození v souboru.  Požádejte uživatele, který vytváří .netmodule prozkoumat.  
  
 Kompilátor nekontroluje .netmodule soubory pro všechny typy poškození.  Nicméně, zkontrolujte, zda všechny cesty ovládacího prvku ve funkci obsahovat příkaz return.  
  
 Další informace najdete v tématu [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).