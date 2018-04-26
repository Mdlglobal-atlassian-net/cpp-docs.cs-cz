---
title: Rutiny zpracování výjimek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3af35bc623b2646e370c9b72ab39fce6e6413081
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="exception-handling-routines"></a>Rutiny zpracování výjimek

Zpracování výjimek funkcí jazyka C++ použijte k obnovení z neočekávané události při spuštění programu.

## <a name="exception-handling-functions"></a>Zpracování výjimek – funkce

|Funkce|Použití|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 zpracování výjimek (C strukturovaná výjimky) jako C++ zadali výjimky|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Nainstalovat rutiny vlastní ukončení má být volána **ukončení**|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instalace funkce vlastní ukončení má být volána **neočekávané**|
|[Ukončení](../c-runtime-library/reference/terminate-crt.md)|Volá automaticky za určitých okolností se po vyvolání výjimky. **Ukončit** volání funkce **abort** nebo funkci, můžete zadat pomocí **set_terminate –**|
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Volání **ukončit** nebo funkci, můžete zadat pomocí **set_unexpected –**. **Neočekávané** funkce ještě není používáno ve aktuální implementace zpracování výjimek Microsoft C++|

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
