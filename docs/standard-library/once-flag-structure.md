---
title: once_flag – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4275b99ada0dbfe1c974446d21862f7fa73aab38
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964493"
---
# <a name="onceflag-structure"></a>once_flag – struktura

Představuje **struktura** , který se používá funkce šablony [call_once –](../standard-library/mutex-functions.md#call_once) zajistit, že inicializace kód je volán pouze jednou, i v případě výskytu více vláken provádění.

## <a name="syntax"></a>Syntaxe

once_flag – struktura {constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag – & – operátor =(const once_flag&);};

## <a name="remarks"></a>Poznámky

`once_flag` **Struktura** nemá výchozí konstruktor.

Objekty typu `once_flag` mohou být vytvořeny, ale nemůže být zkopírován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex – >](../standard-library/mutex.md)<br/>
