---
title: Specifikátor třídy úložiště Auto | Microsoft Docs
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
ms.openlocfilehash: 4054b723c1e44c94be9d112f6bfbd74db8f857ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="auto-storage-class-specifier"></a>Specifikátor třídy úložiště auto
**Automaticky** – specifikátor třídy úložiště deklaruje automatické proměnné, proměnná s místní životnost. **Automaticky** proměnné je viditelná pouze v bloku v kterého je deklarovaná. Prohlášení o **automaticky** proměnné může zahrnovat inicializátory, jak je popsáno v [inicializace](../c-language/initialization.md). Od proměnné s **automaticky** třídy úložiště nejsou inicializovány automaticky, buď explicitně inicializujte je při deklarovat je nebo je přiřadit počáteční hodnoty v příkazech v bloku. Hodnoty Neinicializovaný **automaticky** proměnné nejsou definovány. (Místní proměnná **automaticky** nebo **zaregistrovat** pokaždé, když pochází v oboru, pokud je zadána inicializátoru inicializaci třídy úložiště.)  
  
 Interní **statické** proměnné (statické proměnné s místní nebo rozsah bloku) může být inicializovaný s adresu žádné externí nebo **statické** položku, ale není s adresou jiného **automaticky**  položku, protože adresu **automaticky** položky není konstantní.  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../cpp/auto-keyword.md)