---
title: Robustnost | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4bc7ac76377ef59c9b1f5535f356b35d88a5e4e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220956"
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
