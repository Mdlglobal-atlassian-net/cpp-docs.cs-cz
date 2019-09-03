---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216141"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++Konkrétní**

Určuje jinou předponu, aby se předešlo kolizím názvů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **raw_method_prefix (** "*prefix*" **)**

### <a name="parameters"></a>Parametry

*Směr*\
Předpona, která má být použita.

## <a name="remarks"></a>Poznámky

Vlastnosti a metody nízké úrovně jsou zpřístupněny členskými funkcemi s názvem pomocí výchozí předpony **raw_** , aby se předešlo kolizím názvů s členskými funkcemi pro zpracování chyb na vysoké úrovni.

> [!NOTE]
> Účinky atributu **raw_method_prefix** nejsou beze změny v přítomnosti atributu [raw_interfaces_only](raw-interfaces-only.md) . **Raw_method_prefix** vždy má přednost `raw_interfaces_only` před zadáním předpony. Pokud jsou oba atributy použity ve stejném `#import` příkazu, pak je použita předpona určená atributem **raw_method_prefix** .

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
