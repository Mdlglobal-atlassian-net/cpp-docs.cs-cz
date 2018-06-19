---
title: _inp – _inpw –, _inpd – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a24996fbf2aea97581038bed28297416541ce9da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389846"
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd
Vstupy z portu, bajtů (`_inp`), slova (`_inpw`), nebo slovo, double (`_inpd`).  
  
> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od verze sady Visual Studio 2015, nejsou k dispozici v CRT.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `port`  
 Číslo portu vstupně-výstupní operace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Funkce vrátí bajt, word, nebo double aplikace word číst z `port`. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `_inp`, `_inpw`, A `_inpd` funkce Číst bajt, slovo a dvojitou slova, v uvedeném pořadí, z zadaný vstupní port. Vstupní hodnota může být jakékoli krátké celé číslo bez znaménka v rozsahu 0 – 65 535.  
  
 Protože tyto funkce pro čtení přímo z k portu vstupně-výstupních operací, nelze použít v uživatelském kódu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_inp`|\<conio.h >|  
|`_inpw`|\<conio.h >|  
|`_inpd`|\<conio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)   
 [_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)