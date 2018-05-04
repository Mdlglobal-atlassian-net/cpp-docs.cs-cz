---
title: Abort – funkce | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4acfbb5a0790dec6f7b5770832cc6b09f69a28d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="abort-function"></a>abort – funkce

**Abort** funkce, také deklarován v souboru standardní zahrnout \<stdlib.h >, ukončí programu C++. Rozdíl mezi **ukončete** a **abort** je, že **ukončete** umožňuje zpracování ukončení běhu jazyka C++ proběhla (globální objekt destruktory bude volána), zatímco **abort** program okamžitě ukončí. Další informace najdete v tématu [abort](../c-runtime-library/reference/abort.md) v *referenční dokumentace běhové knihovny*.

## <a name="see-also"></a>Viz také

[Ukončení programu](../cpp/program-termination.md)