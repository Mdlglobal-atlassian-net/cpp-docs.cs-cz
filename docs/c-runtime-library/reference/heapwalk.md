---
title: "_heapwalk – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapwalk
apilocation:
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- heapwalk
- _heapwalk
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 87ff27007734f84b93d0ecb36f637ae22f72098b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="heapwalk"></a>_heapwalk
Prochází halda a vrátí informace o další položky.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime s výjimkou v sestavení pro ladění. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `entryinfo`  
 Vyrovnávací paměť tak, aby obsahovala haldy informace.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_heapwalk`Vrátí jednu z následujících konstanty manifestu typu integer definované v Malloc.h.  
  
 `_HEAPBADBEGIN`  
 Počáteční záhlaví informace neplatná nebo nebyla nalezena.  
  
 `_HEAPBADNODE`  
 Kvůli poškození haldy nebo chybných uzlu byl nalezen.  
  
 `_HEAPBADPTR`  
 `_pentry`pole z `_HEAPINFO` struktura neobsahuje platný ukazatel do haldy nebo `entryinfo` je ukazatel s hodnotou null.  
  
 `_HEAPEND`  
 Úspěšně bylo dosaženo konce haldě.  
  
 `_HEAPEMPTY`  
 Halda nebyla inicializována.  
  
 `_HEAPOK`  
 Žádné chyby, pokud; `entryinfo` se aktualizuje s informacemi o další záznam haldy.  
  
 Kromě toho, pokud dojde k chybě `_heapwalk` nastaví `errno` k `ENOSYS`.  
  
## <a name="remarks"></a>Poznámky  
 `_heapwalk` Funkce pomáhá ladění související s problémy v aplikacích. Funkce haldě procházení jeden záznam za volání, která se provede a vrátí ukazatel na strukturu typu `_HEAPINFO` obsahující informace o další záznam haldy. `_HEAPINFO` Typu, definovaného v Malloc.h, obsahuje následující prvky.  
  
 `int *_pentry`  
 Ukazatel záznam haldy.  
  
 `size_t _size`  
 Velikost haldy položky.  
  
 `int _useflag`  
 Příznak, který určuje, zda položka haldy je používán.  
  
 Volání `_heapwalk` , který vrací `_HEAPOK` ukládá velikost položky v `_size` pole a nastaví `_useflag` pole buď `_FREEENTRY` nebo `_USEDENTRY` (jak jsou definované v Malloc.h konstanty). Chcete-li získat tyto informace o první položku v haldě, předat `_heapwalk` ukazatel na `_HEAPINFO` struktury jehož `_pentry` člen `NULL`. Pokud operační systém nepodporuje `_heapwalk`(například Windows 98), funkce vrátí hodnotu `_HEAPEND` a nastaví `errno` k `ENOSYS`.  
  
 Tato funkce ověří jeho parametru. Pokud `entryinfo` je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `_HEAPBADPTR`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_heapwalk`|\<malloc.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_heapwalk.c  
  
// This program "walks" the heap, starting  
// at the beginning (_pentry = NULL). It prints out each  
// heap entry's use, location, and size. It also prints  
// out information about the overall state of the heap as  
// soon as _heapwalk returns a value other than _HEAPOK  
// or if the loop has iterated 100 times.  
  
#include <stdio.h>  
#include <malloc.h>  
  
void heapdump(void);  
  
int main(void)  
{  
    char *buffer;  
  
    heapdump();  
    if((buffer = (char *)malloc(59)) != NULL)  
    {  
        heapdump();  
        free(buffer);  
    }  
    heapdump();  
}  
  
void heapdump(void)  
{  
    _HEAPINFO hinfo;  
    int heapstatus;  
    int numLoops;  
    hinfo._pentry = NULL;  
    numLoops = 0;  
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&  
          numLoops < 100)  
    {  
        printf("%6s block at %Fp of size %4.4X\n",  
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),  
               hinfo._pentry, hinfo._size);  
        numLoops++;  
    }  
  
    switch(heapstatus)  
    {  
    case _HEAPEMPTY:  
        printf("OK - empty heap\n");  
        break;  
    case _HEAPEND:  
        printf("OK - end of heap\n");  
        break;  
    case _HEAPBADPTR:  
        printf("ERROR - bad pointer to heap\n");  
        break;  
    case _HEAPBADBEGIN:  
        printf("ERROR - bad start of heap\n");  
        break;  
    case _HEAPBADNODE:  
        printf("ERROR - bad node in heap\n");  
        break;  
    }  
}  
```  
  
```Output  
  USED block at 00310650 of size 0100  
  USED block at 00310758 of size 0800  
  USED block at 00310F60 of size 0080  
  FREE block at 00310FF0 of size 0398  
  USED block at 00311390 of size 000D  
  USED block at 003113A8 of size 00B4  
  USED block at 00311468 of size 0034  
  USED block at 003114A8 of size 0039  
...  
  USED block at 00312228 of size 0010  
  USED block at 00312240 of size 1000  
  FREE block at 00313250 of size 1DB0  
OK - end of heap  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [_heapadd –](../../c-runtime-library/heapadd.md)   
 [_heapchk –](../../c-runtime-library/reference/heapchk.md)   
 [_heapmin –](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)