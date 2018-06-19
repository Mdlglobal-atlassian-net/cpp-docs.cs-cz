---
title: _get_FMA3_enable _set_FMA3_enable | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
dev_langs:
- C++
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e9f3058f4b8ebc59ba58460ba122cab063a5059
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399193"
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable _set_FMA3_enable

Získá nebo nastaví příznak určující, zda přechodový matematické funkce s plovoucí desetinnou čárkou knihovny použijte pokyny FMA3 v zkompilování kódu pro X64 platformy.

## <a name="syntax"></a>Syntaxe

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parametry

*Příznak*<br/>
Nastavit na hodnotu 1 pro povolení FMA3 implementace přechodový matematické funkce s plovoucí desetinnou čárkou knihovny na X64 platformy, nebo na 0, budou používat implementace, které nepoužívají FMA3 pokyny.

## <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud jsou povolené FMA3 implementace přechodový matematické funkce knihovny s plovoucí desetinnou čárkou. Jinak hodnota nula.

## <a name="remarks"></a>Poznámky

Použít **_set_FMA3_enable** funkce, které chcete povolit nebo zakázat používání FMA3 pokynů v přechodový matematické s plovoucí desetinnou čárkou funkce knihovny CRT. Návratová hodnota odráží implementace používá po provedení změny. Pokud procesor nepodporuje FMA3 pokyny, tato funkce nelze povolit v knihovně a návratovou hodnotou je nulová. Použití **_get_FMA3_enable** získat aktuální stav knihovny. Ve výchozím nastavení X64 platforem, kód pro spuštění CRT zjistí, zda procesor podporuje FMA3 pokyny a povolí nebo zakáže FMA3 implementace v knihovně.

Protože implementace FMA3 používají různé algoritmy, drobné rozdíly ve výsledku výpočty může být lze zobrazit, pokud jsou zapnutá nebo vypnutá implementace FMA3, nebo mezi počítači, které nemusí být nepodporují FMA3. Další informace najdete v tématu [problémy s plovoucí desetinnou čárkou migrace](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Požadavky

**_Set_FMA3_enable** a **_get_FMA3_enable** funkce jsou dostupné X64 jenom verze CRT.

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<math.h ><br />C++: \<cmath – > nebo \<math.h >|

**_Set_FMA3_enable** a **_get_FMA3_enable** funkce se konkrétní společnosti Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Problémy migrace s plovoucí desetinnou čárkou](../../porting/floating-point-migration-issues.md)<br/>
