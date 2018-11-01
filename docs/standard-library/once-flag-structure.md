---
title: once_flag – struktura
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 004a5545e2eccab83b0846e2ae30b88c8431c99d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481968"
---
# <a name="onceflag-structure"></a>once_flag – struktura

Představuje **struktura** , který se používá funkce šablony [call_once –](../standard-library/mutex-functions.md#call_once) zajistit, že inicializace kód je volán pouze jednou, i v případě výskytu více vláken provádění.

## <a name="syntax"></a>Syntaxe

once_flag – struktura {constexpr once_flag() noexcept;};

## <a name="remarks"></a>Poznámky

`once_flag` **Struktura** nemá výchozí konstruktor.

Objekty typu `once_flag` mohou být vytvořeny, ale nemůže být zkopírován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex – >](../standard-library/mutex.md)<br/>
