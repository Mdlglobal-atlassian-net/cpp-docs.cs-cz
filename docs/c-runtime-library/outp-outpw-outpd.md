---
title: "_outp – _outpw –, _outpd – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
dev_langs: C++
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: edcb3f8da6252705fe494acaa64c623b8a22ed3b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd
Výstupy na port, bajtů (`_outp`), slova (`_outpw`), nebo slovo, double (`_outpd`).  
  
> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od verze sady Visual Studio 2015, nejsou k dispozici v CRT.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _outp(  
unsigned short port,  
int databyte   
);  
unsigned short _outpw(  
unsigned short port,  
unsigned short dataword   
);  
unsigned long _outpd(  
unsigned short port,  
unsigned long dataword   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *port*  
 Číslo portu.  
  
 *databyte dataword*  
 Výstup hodnoty.  
  
## <a name="return-value"></a>Návratová hodnota  
 Funkce vrátí výstupní data. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `_outp`, `_outpw`, A `_outpd` funkce zápis bajtů, slovo a dvojitou slova, v uvedeném pořadí, do zadané výstupní port. *Port* argument může být jakékoli celé číslo bez znaménka v rozsahu 0 – 65 535; *databyte* může být jakékoli celé číslo v rozsahu 0 – 255; a *dataword* může být libovolná hodnota v rozsahu celé číslo, celé číslo bez znaménka krátký a dlouhý číslo bez znaménka, v uvedeném pořadí.  
  
 Protože tyto funkce zapisovat přímo k portu vstupně-výstupních operací, nelze použít v uživatelském kódu v systému Windows NT, Windows 2000, Windows XP a Windows Server 2003. Informace o používání vstupně-výstupních portů v těchto operačních systémů vyhledejte na webu MSDN "Sériové komunikace v Win32".  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_outp`|\<conio.h >|  
|`_outpw`|\<conio.h >|  
|`_outpd`|\<conio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)   
 [_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)