---
title: _ismbbblank, _ismbbblank_l
ms.date: 4/2/2020
api_name:
- _ismbbblank_l
- _ismbbblank
- _o__ismbbblank
- _o__ismbbblank_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: d21b2e41-7206-41f5-85bb-9c9ab4f3e21b
ms.openlocfilehash: 8285a3ae34c3b0fd678e447c76a28495b6f4ffb3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909525"
---
# <a name="_ismbbblank-_ismbbblank_l"></a>_ismbbblank, _ismbbblank_l

Určuje, zda je zadaný vícebajtový znak prázdným znakem.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbbblank(
   unsigned int c
);
int _ismbbblank_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Celé číslo, které se má testovat.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbblank** vrátí nenulovou hodnotu, pokud *c* představuje znak mezery (0x20), znak horizontálního tabulátoru (0x09) nebo znak specifický pro národní prostředí, který se používá k oddělení slov v rámci řádku textu, pro který je **místo** pravda. v opačném případě vrátí 0. **_ismbbblank** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí. **_ismbbblank_l** je totožný s tím rozdílem, že místo toho používá národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbblank**|\<Mbctype. h>|
|**_ismbbblank_l**|\<Mbctype. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
