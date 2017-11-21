---
title: "Funkce zpětného volání používané v prostředí MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.functions
dev_langs: C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4c25693b31359b70ba36fd43394b7074e464c954
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="callback-functions-used-by-mfc"></a>Funkce zpětného volání používané v prostředí MFC
Zobrazí tři funkce zpětného volání v knihovny Microsoft Foundation Class. Tyto funkce zpětného volání, které se předávají do [metodu CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [metodu CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), a [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Všimněte si, že všechny funkce zpětného volání musí zachycují výjimky MFC před vrácením Windows, protože nemůže být vyvolány výjimky napříč hranicemi zpětného volání. Další informace o výjimkách, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  

|Název||  
|----------|-----------------|  
|[Funkce zpětného volání pro metodu CDC::EnumObjects](#enum_objects)||  
|[Funkce zpětného volání pro metodu CDC::GrayString](#graystring)||
|[Funkce zpětného volání pro metodu CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h 

## <a name="enum_objects"></a>Funkce zpětného volání pro metodu CDC::EnumObjects
*ObjectFunc* název je zástupný symbol pro název funkce zadané aplikace.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLogObject*  
 Odkazuje na [logpen –](../../mfc/reference/logpen-structure.md) nebo [logbrush –](../../mfc/reference/logbrush-structure.md) datová struktura, která obsahuje informace o logické atributy objektu.  
  
 `lpData`  
 Předaný body k datům zadané aplikace `EnumObjects` funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí funkce zpětného volání `int`. Tato vrátit hodnotu definovaný uživatelem. Pokud funkce zpětného volání, vrátí hodnotu 0, `EnumObjects` zastaví výčtu již v rané fázi.  
  
### <a name="remarks"></a>Poznámky  
 Musí být exportován skutečný název.  
  
## <a name="graystring"></a>Funkce zpětného volání pro metodu CDC::GrayString
*OutputFunc* je zástupný symbol pro název funkce zpětného volání zadané aplikace.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `hDC`  
 Identifikuje kontextu zařízení paměti bitmapa alespoň šířky a výšky určeného `nWidth` a `nHeight` k `GrayString`.  
  
 `lpData`  
 Odkazuje na řetězec znaků, který chcete kreslit.  
  
 `nCount`  
 Určuje počet znaků, který má výstup.  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce zpětného volání vrácená hodnota musí být **TRUE** čímž indikuje úspěšné provedení; v opačném případě je **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Funkce zpětného volání (*OutputFunc*) musí kreslení obrázku relativně k souřadnice (0,0) místo (*x*, *y*).  

## <a name="setabortproc"></a>Funkce zpětného volání pro metodu CDC::SetAbortProc
Název *AbortFunc* je zástupný symbol pro název funkce zadané aplikace.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
### <a name="parameters"></a>Parametry  
 *hPr*  
 Identifikuje kontextu zařízení.  
  
 `code`  
 Určuje, zda došlo k chybě. Pokud nedošlo k žádné chybě je 0. Je **SP_OUTOFDISK** Pokud správce tisku právě nedostatek místa na disku a více místa na disku, bude k dispozici, pokud aplikace čeká. Pokud `code` je **SP_OUTOFDISK**, aplikace nemá na zrušení tiskové úlohy. Pokud ne, musíte yield správce tisku voláním **PeekMessage** nebo **GetMessage** funkce systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota funkce obslužné rutiny přerušení je nenulové hodnoty, pokud se tisková úloha má pokračovat a 0 Pokud je zrušená.  
  
### <a name="remarks"></a>Poznámky  
 Skutečný název musí být exportován, jak je popsáno v části poznámky [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).  
 
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md) [metodu CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects) [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc) [metodu CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)

