---
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
api_name:
- __wgetmainargs
- __getmainargs
api_location:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 01658c6146706d8ea7bfd70d002efcfff88031b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171590"
---
# <a name="__getmainargs-__wgetmainargs"></a>__getmainargs, __wgetmainargs

Vyvolá analýzu příkazového řádku a zkopíruje argumenty pro `main()` zpět prostřednictvím předaných ukazatelů.

## <a name="syntax"></a>Syntaxe

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char *** _Env,
   int _DoWildCard,
_startupinfo * _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t ***_Env,
   int _DoWildCard,
   _startupinfo * _StartInfo)
```

#### <a name="parameters"></a>Parametry

`_Argc`<br/>
Celé číslo, které obsahuje počet argumentů, které následují v `argv`. Parametr `argc` je vždy větší nebo roven 1.

`_Argv`<br/>
Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv[0]` je příkaz, se kterým se program vyvolá, argv [1] je první argument příkazového řádku a tak dále, dokud argv [argc], které je vždycky **null**. První argument příkazového řádku je vždycky `argv[1]` a poslední z nich je `argv[argc - 1]`.

`_Env`<br/>
Pole řetězců, které reprezentují proměnné nastavené v uživatelském prostředí. Toto pole je ukončeno položkou **null** .

`_DoWildCard`<br/>
Celé číslo, které je-li nastaveno na hodnotu 1, rozbalí zástupné znaky v argumentech příkazového řádku nebo pokud je nastaveno na hodnotu 0, neprovede nic.

`_StartInfo`<br/>
Další informace, které mají být předány knihovně DLL CRT.

## <a name="return-value"></a>Návratová hodnota

0, pokud bylo úspěšné; záporná hodnota v případě neúspěchu.

## <a name="remarks"></a>Poznámky

Používejte `__getmainargs` na jiných než různých znakových platformách a `__wgetmainargs` na platformách s velkým znakem (Unicode).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|
