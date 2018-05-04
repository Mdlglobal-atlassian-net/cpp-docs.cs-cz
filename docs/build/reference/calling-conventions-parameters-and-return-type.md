---
title: Konvence volání, parametry a návratový typ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5680e4616a2af46066175928216022211bcb288f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="calling-conventions-parameters-and-return-type"></a>Konvence volání, parametry a návratový typ
Pomocná rutina prototypu je:  
  
```  
FARPROC WINAPI __delayLoadHelper2(   
   PCImgDelayDescr pidd,  
   FARPROC * ppfnIATEntry  
);  
```  
  
 kde:  
  
 `pidd`  
 A `const` ukazatel na `ImgDelayDescr` (viz delayimp.h), který obsahuje posunutí různých týkající se importu dat, časové razítko pro informace o vazbě a sadu atributů, které poskytují další informace o obsahu, popisovače. Aktuálně je pouze jeden atribut `dlattrRva`, což naznačuje, že adresy v popisovači jsou relativní virtuální adresy (na rozdíl od virtuální adresy).  
  
 Pro definici `PCImgDelayDescr` struktury najdete v tématu [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md).  
  
 `ppfnIATEntry`  
 Ukazatel na pozici v zatížení zpoždění tabulka importních adres (IAT) aktualizovat s adresou importované funkce. Pomocné rutiny je potřeba úložiště se stejnou hodnotou, bude se vrátí do tohoto umístění.  
  
## <a name="expected-return-values"></a>Očekávaný návratové hodnoty  
 Pokud funkci úspěšné, vrátí adresu importované funkce.  
  
 V případě selhání funkce vyvolá výjimku a vrátí hodnotu 0. Mohou být vyvolány tři typy výjimek:  
  
-   Neplatný parametr, který se stane, když atributy v `pidd` nejsou správně zadán.  
  
-   `LoadLibrary` v zadané DLL se nezdařilo.  
  
-   Selhání `GetProcAddress`.  
  
 Je vaší povinností zpracování těchto výjimek.  
  
## <a name="remarks"></a>Poznámky  
 Konvence volání pro pomocné funkce je `__stdcall`. Typ vrácené hodnoty není relevantní, takže FARPROC se používá. Tato funkce má C propojení.  
  
 Návratová hodnota pomocná zatížení zpoždění musí být uložen v umístění ukazatele předaný funkci, pokud chcete, aby vaše pomocnou rutinou má být použit jako oznámení háku. V takovém případě váš kód je zodpovědná za vyhledávání ukazatele příslušnou funkci vrátit. Převodu kód, který generuje linkeru pak trvá tento návratovou hodnotu jako skutečné cíl importu a přejde přímo na.  
  
## <a name="sample"></a>Ukázka  
 Následující kód ukazuje, jak implementovat funkce háku jednoduché.  
  
```  
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)  
{  
    switch (dliNotify) {  
        case dliStartProcessing :  
  
            // If you want to return control to the helper, return 0.  
            // Otherwise, return a pointer to a FARPROC helper function  
            // that will be used instead, thereby bypassing the rest   
            // of the helper.  
  
            break;  
  
        case dliNotePreLoadLibrary :  
  
            // If you want to return control to the helper, return 0.  
            // Otherwise, return your own HMODULE to be used by the   
            // helper instead of having it call LoadLibrary itself.  
  
            break;  
  
        case dliNotePreGetProcAddress :  
  
            // If you want to return control to the helper, return 0.  
            // If you choose you may supply your own FARPROC function   
            // address and bypass the helper's call to GetProcAddress.  
  
            break;  
  
        case dliFailLoadLib :   
  
            // LoadLibrary failed.  
            // If you don't want to handle this failure yourself, return 0.  
            // In this case the helper will raise an exception   
            // (ERROR_MOD_NOT_FOUND) and exit.  
            // If you want to handle the failure by loading an alternate   
            // DLL (for example), then return the HMODULE for   
            // the alternate DLL. The helper will continue execution with   
            // this alternate DLL and attempt to find the  
            // requested entrypoint via GetProcAddress.  
  
            break;  
  
        case dliFailGetProc :  
  
            // GetProcAddress failed.  
            // If you don't want to handle this failure yourself, return 0.  
            // In this case the helper will raise an exception   
            // (ERROR_PROC_NOT_FOUND) and exit.  
            // If you choose you may handle the failure by returning   
            // an alternate FARPROC function address.  
  
            break;  
  
        case dliNoteEndProcessing :   
  
            // This notification is called after all processing is done.   
            // There is no opportunity for modifying the helper's behavior  
            // at this point except by longjmp()/throw()/RaiseException.   
            // No return value is processed.  
  
            break;  
  
        default :  
  
            return NULL;  
    }  
  
    return NULL;  
}  
  
/*   
and then at global scope somewhere  
PfnDliHook __pfnDliNotifyHook2 = delayHook;  
*/  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní informace o podpůrné funkci](../../build/reference/understanding-the-helper-function.md)