---
title: "Abort – funkce | Microsoft Docs"
ms.custom: 
ms.date: 12/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fcd54b9aacf4eaba4bb5acfb115943225aa0efa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="abort-function"></a>abort – funkce

**Abort** funkce, také deklarován v souboru standardní zahrnout STDLIB. H, ukončí programu C++. Rozdíl mezi **ukončete** a **abort** je, že **ukončete** umožňuje zpracování ukončení běhu jazyka C++ proběhla (globální objekt destruktory bude volána), zatímco **abort** program okamžitě ukončí. Další informace najdete v tématu [abort](../c-runtime-library/reference/abort.md) v *referenční dokumentace běhové knihovny*.

## <a name="see-also"></a>Viz také

[Ukončení programu](../cpp/program-termination.md)