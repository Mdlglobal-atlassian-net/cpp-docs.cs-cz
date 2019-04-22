---
title: raw_method_prefix
ms.date: 03/27/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 963e04752dcb797343550d9b89f778bfe0e8a593
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021408"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**Specifické pro C++**

Určuje jinou předponu vyhnete kolize názvů.

## <a name="syntax"></a>Syntaxe

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>Parametry

*Prefix*<br/>
Předpona, která má být použit.

## <a name="remarks"></a>Poznámky

Nízké úrovně vlastnosti a metody vystaveny členským funkcím pojmenovaným s předponou výchozí **raw_** k vyhnete kolize názvů s vysoké úrovně členské funkce zpracování chyb.

> [!NOTE]
> Účinky **raw_method_prefix –** atribut se nezmění přítomností [raw_interfaces_only](raw-interfaces-only.md) atribut. **Raw_method_prefix –** vždy má přednost před `raw_interfaces_only` v určeném předponu. Pokud oba atributy jsou používány ve stejném `#import` příkaz a pak podle Zadaná předpona **raw_method_prefix –** atribut se používá.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)