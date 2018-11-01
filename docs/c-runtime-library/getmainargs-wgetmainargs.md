---
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 625b3437bc922f3ca73c150fa14adf1f57567abb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504578"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs

Vyvolá parsování příkazového řádku a zkopíruje argumenty, které mají `main()` zpět prostřednictvím předaný ukazatele.

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
Celé číslo obsahující počet argumentů, které následují v `argv`. Parametr `argc` je vždy větší nebo roven 1.

`_Argv`<br/>
Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv[0]` příkaz, kterým je program vyvolán, argv [1] je první argument příkazového řádku a tak dále, dokud argv [argc], což je vždy **NULL**. První argument příkazového řádku je vždy `argv[1]` a poslední je `argv[argc - 1]`.

`_Env`<br/>
Pole řetězců, které představují proměnné nastavené v uživatelském prostředí. Toto pole je ukončeno prvkem **NULL** položka.

`_DoWildCard`<br/>
Celé číslo, pokud na hodnotu 1 rozšíří zástupné znaky v argumentech příkazového řádku, nebo pokud nastaveno na 0 nemá žádný účinek.

`_StartInfo`<br/>
Další informace, které se mají předat CRT knihovny DLL.

## <a name="return-value"></a>Návratová hodnota

0 v případě úspěchu; zápornou hodnotu, pokud není úspěšné.

## <a name="remarks"></a>Poznámky

Použití `__getmainargs` na platformách jiných širokého znaku a `__wgetmainargs` na platformách širokého znaku (Unicode).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|