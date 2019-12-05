---
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: dee75bf5b16b5fe5b619444f7f2736010bb42a84
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857804"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable, _set_FMA3_enable

Získá nebo nastaví příznak, který určuje, zda funkce knihovny s plovoucí desetinnou čárkou transcendentní matematických funkcí používá instrukce FMA3 v kódu kompilovaném pro platformy x64.

## <a name="syntax"></a>Syntaxe

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parametry

*příznaků*<br/>
Nastavte na hodnotu 1, pokud chcete povolit FMA3 implementace knihovny plovoucí desetinné čárky transcendentní na platformách x64 nebo 0, chcete-li použít implementace, které nepoužívají instrukce FMA3.

## <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud jsou povoleny implementace FMA3 funkce knihovny plovoucí desetinné čárky transcendentní. V opačném případě nula.

## <a name="remarks"></a>Poznámky

Pomocí funkce **_set_FMA3_enable** povolíte nebo zakážete použití instrukcí FMA3 ve funkcích matematického plovoucí desetinné čárky transcendentní v knihovně CRT. Vrácená hodnota odráží implementaci, která se používá po změně. Pokud procesor nepodporuje instrukce FMA3, tato funkce je nemůže povolit v knihovně a vrácená hodnota je nula. Pomocí **_get_FMA3_enable** získat aktuální stav knihovny. Ve výchozím nastavení na platformách x64 detekuje spouštěcí kód CRT, zda procesor podporuje instrukce FMA3 a povoluje nebo zakazuje implementace FMA3 v knihovně.

Vzhledem k tomu, že implementace FMA3 používají různé algoritmy, mohou být nepatrné rozdíly ve výsledku výpočtů pozorovatelné, pokud jsou povolené nebo zakázané implementace FMA3, nebo mezi počítači, které dělají nebo nepodporují FMA3. Další informace najdete v tématu [problémy s migrací s plovoucí](../../porting/floating-point-migration-issues.md)desetinnou čárkou.

## <a name="requirements"></a>Požadavky

Funkce **_set_FMA3_enable** a **_get_FMA3_enable** jsou k dispozici pouze ve verzích x64 CRT.

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<Math. h ><br />C++: \<cmath > nebo \<Math. h >|

Funkce **_set_FMA3_enable** a **_get_FMA3_enable** jsou specifické pro společnost Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Problémy migrace s plovoucí desetinnou čárkou](../../porting/floating-point-migration-issues.md)<br/>
