---
title: _get_FMA3_enable _set_FMA3_enable
ms.date: 04/05/2018
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
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 19eabc3b5a11246d5b0056bdafbb169e2a7de9f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544362"
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable _set_FMA3_enable

Získá nebo nastaví příznak určující, zda Transcendentní matematické funkce s plovoucí desetinnou čárkou knihovny postupujte podle pokynů FMA3 v kódu zkompilovaném pro X64 platformy.

## <a name="syntax"></a>Syntaxe

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parametry

*Příznak*<br/>
Nastavit na hodnotu 1 pro povolení implementace FMA3 Transcendentní matematické funkce s plovoucí desetinnou čárkou knihovny na X64 platformy nebo 0 pro použití implementace, které nepoužívají FMA3 pokyny.

## <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud jsou povolené FMA3 implementace Transcendentní matematické funkce s plovoucí desetinnou čárkou knihovny. Jinak, nula.

## <a name="remarks"></a>Poznámky

Použít **_set_FMA3_enable** funkci chcete povolit nebo zakázat použití FMA3 instrukcí v Transcendentní matematické funkce s plovoucí desetinnou čárkou v knihovně CRT. Návratová hodnota odráží implementace používá po provedení změny. Pokud procesor nepodporuje FMA3 pokyny, tato funkce je nemůže povolit v knihovně a vrácená hodnota je nula. Použití **_get_FMA3_enable** získat aktuální stav knihovny. Ve výchozím nastavení X64 platformy, CRT spouštěcí kód zjistí, jestli CPU podporuje FMA3 pokyny a povolí nebo zakáže FMA3 implementace v knihovně.

Implementace FMA3 používat různé algoritmy, mírné rozdíly v výsledek výpočtů může být pozorovat při FMA3 implementace jsou zapnutá nebo vypnutá, nebo mezi počítači, které nemají nebo nepodporují FMA3. Další informace najdete v tématu [problémy migrace s plovoucí desetinnou čárkou](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Požadavky

**_Set_FMA3_enable** a **_get_FMA3_enable** funkce jsou dostupné jenom v X64 verze CRT.

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<math.h ><br />Jazyk C++: \<cmath > nebo \<math.h >|

**_Set_FMA3_enable** a **_get_FMA3_enable** funkce jsou specifické pro Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Problémy migrace s plovoucí desetinnou čárkou](../../porting/floating-point-migration-issues.md)<br/>
