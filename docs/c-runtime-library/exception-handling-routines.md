---
title: Rutiny zpracování výjimek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eea92c5bfdb54b6c15ae2ae643b2d23b397a3bf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389072"
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

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
