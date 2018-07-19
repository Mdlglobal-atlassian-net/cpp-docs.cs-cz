---
title: Funkce zpětného volání používané v prostředí MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96db2ea0c28e14f7a8e614d94e18cd3fad3cda53
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339007"
---
# <a name="callback-functions-used-by-mfc"></a>Funkce zpětného volání používané v prostředí MFC
Zobrazí tři funkce zpětného volání v knihovny Microsoft Foundation Class. Tyto funkce zpětného volání jsou předány [metodu CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [metodu CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), a [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Všimněte si, že všechny funkce zpětného volání musí zachycují výjimky MFC před vrácením Windows, protože výjimky nejde vyvolat přes hranice zpětného volání. Další informace o výjimkách, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  

|Název||  
|----------|-----------------|  
|[Funkce zpětného volání pro metodu CDC::EnumObjects](#enum_objects)||  
|[Funkce zpětného volání pro metodu CDC::GrayString](#graystring)||
|[Funkce zpětného volání pro metodu CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h 

## <a name="enum_objects"></a> Funkce zpětného volání pro metodu CDC::EnumObjects
*ObjectFunc* název je zástupný symbol pro název funkce poskytované aplikací.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLogObject*  
 Odkazuje [logpen –](../../mfc/reference/logpen-structure.md) nebo [logbrush –](../../mfc/reference/logbrush-structure.md) datová struktura, která obsahuje informace o logické atributy objektu.  
  
 *lpData*  
 Body k datům poskytované aplikací předaný `EnumObjects` funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce zpětného volání vrátí **int**. Tato návratovou hodnotu definovaný uživatelem. Pokud funkce zpětného volání vrátí hodnotu 0, `EnumObjects` zastaví výčet již v rané fázi.  
  
### <a name="remarks"></a>Poznámky  
 Skutečný název musí být exportován.  
  
## <a name="graystring"></a>  Funkce zpětného volání pro metodu CDC::GrayString
*OutputFunc* je zástupný symbol pro název funkce poskytované aplikací zpětného volání.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>Parametry  
 *hDC*  
 Určuje kontext zařízení paměti s rastrový obrázek alespoň šířku a výšku určené `nWidth` a `nHeight` k `GrayString`.  
  
 *lpData*  
 Odkazuje na řetězec znaků, který chcete kreslit.  
  
 *nCount*  
 Určuje počet znaků výstupu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota funkce zpětného volání musí být TRUE, čímž indikuje úspěšné provedení; v opačném případě je FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Funkce zpětného volání (*OutputFunc*) musí vykreslení obrázku vzhledem k souřadnice (0,0) místo (*x*, *y*).  

## <a name="setabortproc"></a>  Funkce zpětného volání pro metodu CDC::SetAbortProc
Název *AbortFunc* je zástupný symbol pro název funkce poskytované aplikací.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
### <a name="parameters"></a>Parametry  
 *hPr*  
 Určuje kontext zařízení.  
  
 *kód*  
 Určuje, zda došlo k chybě. To je 0, pokud nedojde k žádné chybě. Je SP_OUTOFDISK Pokud správce tisku právě volné místo na disku a bude k dispozici více místa na disku aplikace čeká. Pokud *kód* je SP_OUTOFDISK, aplikace nemusí přerušit tiskové úlohy. Pokud tomu tak není, musí poskytovat správce tisku pomocí volání `PeekMessage` nebo `GetMessage` funkce Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota funkce obslužné rutiny přerušení je nenulová, pokud je chcete pokračovat, tiskové úlohy a 0 Pokud bude zrušen.  
  
### <a name="remarks"></a>Poznámky  
 Skutečný název musí být exportován, jak je popsáno v části poznámky [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).  
 
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md) [metodu CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects) [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc) [metodu CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)

