---
title: Vývoj vlastní pomocné funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76172804cc271a740244d06e791db35d534c69e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="developing-your-own-helper-function"></a>Vývoj vlastní pomocné funkce
Můžete zadat vlastní verzi rutiny udělat konkrétní zpracování na základě názvů importy nebo knihovny DLL. To provést dvěma způsoby: kódování vlastní, případně založená na zadaný kód, nebo jenom zapojování poskytnutá verze pomocí háky oznámení podrobné dříve.  
  
 Kód vlastní  
 Toto je docela jednoduchá, vzhledem k tomu, že zadaný kód můžete v podstatě použijte jako vodítko pro novou. Samozřejmě je potřeba dodržovat konvence volání a pokud se obnoví převody generované linkeru, musí vracet správné funkce ukazatel. Jednou v kódu, můžete to udělat podstatě všechno za účelem uspokojení volání nebo získejte z volání.  
  
 Použít spuštění zpracování oznámení háku  
 Pravděpodobně bude nejjednodušší stačí zadat nový ukazatel funkce háku uživatelem zadané oznámení, která přijímá stejné hodnoty jako výchozí pomocná na dliStartProcessing oznámení. V tomto bodě funkce háku se v podstatě stát nové funkce pomocné rutiny, jak bude úspěšné vrátit do pomocné rutiny výchozí vynechat všechny další zpracování ve výchozím nastavení pomocníka.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)