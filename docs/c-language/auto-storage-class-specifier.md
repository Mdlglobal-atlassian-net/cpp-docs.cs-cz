---
title: Specifikátor třídy úložiště auto
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 6bd36fd534602a5a4df95047a830058e8c5ef163
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147006"
---
# <a name="auto-storage-class-specifier"></a>Specifikátor třídy úložiště auto

**Automaticky** – specifikátor třídy úložiště deklaruje automatickou proměnnou, proměnná má místní dobu platnosti. **Automaticky** proměnná je viditelná pouze v bloku ve kterém je deklarována. Deklarace **automaticky** proměnných mohou obsahovat inicializátory, jak je popsáno v [inicializace](../c-language/initialization.md). Od proměnné s **automaticky** třídu úložiště nejsou inicializovány automaticky, které byste je inicializovat explicitně při deklaraci nebo jim počáteční hodnoty v příkazech v rámci bloku přiřadit. Hodnoty neinicializovaných **automaticky** proměnné nejsou definovány. (Místní proměnná **automaticky** nebo **zaregistrovat** úložiště třída je inicializována pokaždé, když je v oboru, pokud je uveden inicializátor.)

Interní **statické** proměnné (statická proměnná s místním nebo rozsahem bloku) lze inicializovat adresou jakékoli vnější nebo **statické** položky, ale nikoli adresou jiné **automaticky**  položky, protože adresa **automaticky** položka není konstantní.

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../cpp/auto-keyword.md)
