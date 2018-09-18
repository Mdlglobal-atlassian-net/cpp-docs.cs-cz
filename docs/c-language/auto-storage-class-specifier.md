---
title: Auto – specifikátor třídy úložiště | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca42eb26cc6bb08cd8a05e31b23e004b1cbeb8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057428"
---
# <a name="auto-storage-class-specifier"></a>Specifikátor třídy úložiště auto

**Automaticky** – specifikátor třídy úložiště deklaruje automatickou proměnnou, proměnná má místní dobu platnosti. **Automaticky** proměnná je viditelná pouze v bloku ve kterém je deklarována. Deklarace **automaticky** proměnných mohou obsahovat inicializátory, jak je popsáno v [inicializace](../c-language/initialization.md). Od proměnné s **automaticky** třídu úložiště nejsou inicializovány automaticky, které byste je inicializovat explicitně při deklaraci nebo jim počáteční hodnoty v příkazech v rámci bloku přiřadit. Hodnoty neinicializovaných **automaticky** proměnné nejsou definovány. (Místní proměnná **automaticky** nebo **zaregistrovat** úložiště třída je inicializována pokaždé, když je v oboru, pokud je uveden inicializátor.)

Interní **statické** proměnné (statická proměnná s místním nebo rozsahem bloku) lze inicializovat adresou jakékoli vnější nebo **statické** položky, ale nikoli adresou jiné **automaticky**  položky, protože adresa **automaticky** položka není konstantní.

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../cpp/auto-keyword.md)