---
title: Abort – funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: 3e5679ce718c564ee40fb07b676756ef79344a99
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403619"
---
# <a name="abort-function"></a>abort – funkce

**Přerušit** deklarovaná také ve standardním vloženém souboru \<stdlib.h >, ukončuje program jazyka C++. Rozdíl mezi `exit` a **přerušit** je, že `exit` umožňuje zpracování ukončení za běhu jazyka C++ uskutečnit (globální objekt zavolány destruktory), zatímco **přerušit** Ukončí program okamžitě. Další informace najdete v tématu [přerušit](../c-runtime-library/reference/abort.md) v *Run-Time Library Reference*.

## <a name="see-also"></a>Viz také:
[Ukončení programu](../cpp/program-termination.md)