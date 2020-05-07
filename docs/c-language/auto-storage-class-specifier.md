---
title: Specifikátor třídy úložiště auto
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 6bd36fd534602a5a4df95047a830058e8c5ef163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313464"
---
# <a name="auto-storage-class-specifier"></a>Specifikátor třídy úložiště auto

Specifikátor třídy úložiště **auto** deklaruje automatickou proměnnou a proměnnou s místní životností. Proměnná **auto** je viditelná pouze v bloku, ve kterém je deklarována. Deklarace **automatických** proměnných mohou obsahovat inicializátory, jak je popsáno v tématu [inicializace](../c-language/initialization.md). Vzhledem k tomu, že proměnné s třídou **automatického** úložiště nejsou inicializovány automaticky, měli byste je buď explicitně inicializovat při jejich deklaraci, nebo je přiřadit počáteční hodnoty v příkazech v rámci bloku. Hodnoty neinicializovaných **automatických** proměnných nejsou definovány. (Místní proměnná třídy úložiště **auto** nebo **Register** je inicializována pokaždé, když se v oboru nachází, pokud je zadán inicializátor.)

Vnitřní **statickou** proměnnou (statickou proměnnou s místním nebo rozsahem bloku) lze inicializovat s adresou libovolné externí nebo **statické** položky, ale ne s adresou jiné položky **auto** , protože adresa **Automatické** položky není konstanta.

## <a name="see-also"></a>Viz také

[auto – klíčové slovo](../cpp/auto-keyword.md)
