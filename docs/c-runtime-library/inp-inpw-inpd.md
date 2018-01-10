---
title: "_inp – _inpw –, _inpd – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15fa7169f46e84cf60e1b869e5eb68a392b16a3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd
Vstupy z portu, bajtů (`_inp`), slova (`_inpw`), nebo slovo, double (`_inpd`).  
  
> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od verze sady Visual Studio 2015, nejsou k dispozici v CRT.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
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
  
 Protože tyto funkce pro čtení přímo z k portu vstupně-výstupních operací, nemusí být použít v uživatelském kódu v systému Windows NT, Windows 2000, Windows XP a Windows Server 2003.  
  
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