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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: d21b2e41-7206-41f5-85bb-9c9ab4f3e21b
ms.openlocfilehash: 819ea45bb9d5775bb59764b587a75e368fa0e80d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343750"
---
# <a name="_ismbbblank-_ismbbblank_l"></a>_ismbbblank, _ismbbblank_l

Určuje, zda je zadaný vícebajtový znak prázdný znak.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*<br/>
Celé číslo, které má být testováno.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbblank** vrátí nenulovou hodnotu, pokud *c* představuje znak mezery (0x20), znak vodorovné tabulátoru (0x09) nebo znak specifický pro národní prostředí, který se používá k oddělení slov v řádku textu, pro který **je mezera** true; v opačném případě vrátí 0. **_ismbbblank** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí. **_ismbbblank_l** je identická s tím rozdílem, že místo toho používá národní prostředí, které je předáno. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbblank**|\<mbctype.h>|
|**_ismbbblank_l**|\<mbctype.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
