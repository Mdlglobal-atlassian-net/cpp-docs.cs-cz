---
title: Robustnost
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 9244ba430efab01cd82b8ad773ad669470d67cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454701"
---
# <a name="robustness"></a>Robustnost

Následující funkce běhové knihovny jazyka C umožňuje zvýšit robustnost programu.

## <a name="run-time-robustness-functions"></a>Funkce odolnosti za běhu

|Funkce|Použití|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Přenese ovládací prvek na váš mechanismus zpracování chyb, pokud **nové** operátor selže přidělování paměti.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Obslužné rutiny výjimky Win32 (strukturované výjimky jazyka C) jako C++ zadané výjimky.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Nainstaluje vlastní funkci ukončení má být volána [ukončit](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Nainstaluje vlastní funkci ukončení má být volána [neočekávané](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](https://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)<br/>
