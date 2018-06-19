---
title: __getmainargs __wgetmainargs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13707791b78de2c000535d60ed3f298046e4576c
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451283"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs
Vyvolá analýze příkazového řádku a zkopíruje argumenty, které mají `main()` zpět prostřednictvím předaný ukazatele.  
  
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
 `_Argc`  
 Celé číslo, které obsahuje počet argumentů, které následují v `argv`. Parametr `argc` je vždy větší nebo roven 1.  
  
 `_Argv`  
 Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv[0]` je příkaz, ke které je voláno program, argv – [1] je první argument příkazového řádku a tak dále, dokud argv – [argc –], který je vždycky **NULL**. První argument příkazového řádku je vždy `argv[1]` a je poslední `argv[argc - 1]`.  
  
 `_Env`  
 Pole řetězců, které představují proměnné nastavit v prostředí uživatele. Toto pole je ukončena **NULL** položku.  
  
 `_DoWildCard`  
 Celé číslo, pokud nastavenou na 1 rozšíří zástupné znaky v argumentech příkazového řádku, nebo pokud nastavení na hodnotu 0 se nic nestane.  
  
 `_StartInfo`  
 Další informace, které mají být předány CRT knihovny DLL.  
  
## <a name="return-value"></a>Návratová hodnota  
 0 v případě úspěšného; Záporná Pokud neúspěšně.  
  
## <a name="remarks"></a>Poznámky  
 Použití `__getmainargs` na jiné úrovni znak platformách a `__wgetmainargs` na platformách široká charakterová (Unicode).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__getmainargs|internal.h|  
|__wgetmainargs|internal.h|