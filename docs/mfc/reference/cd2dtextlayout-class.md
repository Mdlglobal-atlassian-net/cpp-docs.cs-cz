---
title: "Třída CD2DTextLayout | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs: C++
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bf5a4b554f3ee06c9f7aab60fe615ef9be0e544a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout – třída
Obálka pro IDWriteTextLayout.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Vytvoří objekt CD2DTextLayout.|  
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|Destruktor. Voláno, když je zničen objektu D2D text rozložení.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextLayout::Create](#create)|Vytvoří CD2DTextLayout. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextLayout::Destroy](#destroy)|Zničí CD2DTextLayout objektu. (Přepisuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextLayout::Get](#get)|Vrátí IDWriteTextLayout rozhraní|  
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Zkopíruje název rodiny písem textu na zadané pozici.|  
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Získá název národního prostředí textu na zadané pozici.|  
|[CD2DTextLayout::IsValid](#isvalid)|Ověří platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextLayout::ReCreate](#recreate)|Znovu vytvoří CD2DTextLayout. (Přepisuje [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nastaví název rodiny ukončené hodnotou null písmo pro text v rozsahu zadaný text|  
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Nastaví název národního prostředí pro text v rozsahu zadaný text.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextLayout::Operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Vrátí IDWriteTextLayout rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Ukazatel IDWriteTextLayout.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextlayout"></a>CD2DTextLayout:: ~ CD2DTextLayout  
 Destruktor. Voláno, když je zničen objektu D2D text rozložení.  
  
```  
virtual ~CD2DTextLayout();
```  
  
##  <a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout  
 Vytvoří objekt CD2DTextLayout.  
  
```  
CD2DTextLayout(
    CRenderTarget* pParentTarget,  
    const CString& strText,  
    CD2DTextFormat& textFormat,  
    const CD2DSizeF& sizeMax,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `strText`  
 CString objekt, který obsahuje řetězec, který má-li vytvořit nový objekt CD2DTextLayout z.  
  
 `textFormat`  
 CString objekt, který obsahuje formát, který se vztahuje na řetězec.  
  
 `sizeMax`  
 Velikost pole rozložení.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>CD2DTextLayout::Create  
 Vytvoří CD2DTextLayout.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DTextLayout::Destroy  
 Zničí CD2DTextLayout objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>CD2DTextLayout::Get  
 Vrátí IDWriteTextLayout rozhraní  
  
```  
IDWriteTextLayout* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IDWriteTextLayout nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName  
 Zkopíruje název rodiny písem textu na zadané pozici.  
  
```  
CString GetFontFamilyName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `currentPosition`  
 Pozice text, který chcete prozkoumat.  
  
 `textRange`  
 Rozsah text, který má stejné formátování jako text na pozici určeného currentPosition. To znamená, že má spustit přesný formátování jako pozice zadána, včetně, ale bez omezení na název rodiny písem.  
  
### <a name="return-value"></a>Návratová hodnota  
 CString objekt, který obsahuje aktuální název rodiny písem.  
  
##  <a name="getlocalename"></a>CD2DTextLayout::GetLocaleName  
 Získá název národního prostředí textu na zadané pozici.  
  
```  
CString GetLocaleName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `currentPosition`  
 Pozice text, který chcete zkontrolovat.  
  
 `textRange`  
 Rozsah text, který má stejné formátování jako text na pozici určeného currentPosition. To znamená, že má spustit přesný formátování jako pozice zadána, včetně bez omezení na název národního prostředí.  
  
### <a name="return-value"></a>Návratová hodnota  
 CString objekt, který obsahuje název aktuální národní prostředí.  
  
##  <a name="isvalid"></a>CD2DTextLayout::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout  
 Ukazatel IDWriteTextLayout.  
  
```  
IDWriteTextLayout* m_pTextLayout;  
```  
  
##  <a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::Operator IDWriteTextLayout *  
 Vrátí IDWriteTextLayout rozhraní  
  
```  
operator IDWriteTextLayout*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IDWriteTextLayout nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="recreate"></a>CD2DTextLayout::ReCreate  
 Znovu vytvoří CD2DTextLayout.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName  
 Nastaví název rodiny ukončené hodnotou null písmo pro text v rozsahu zadaný text  
  
```  
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pwzFontFamilyName`  
 Název rodiny písem, která se vztahují na celou textového řetězce v rozsahu určeném rozsahu textRange  
  
 `textRange`  
 Rozsah text, pro kterou platí tato změna  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. Jinak vrátí hodnotu FALSE  
  
##  <a name="setlocalename"></a>CD2DTextLayout::SetLocaleName  
 Nastaví název národního prostředí pro text v rozsahu zadaný text.  
  
```  
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pwzLocaleName`  
 Název řetězce ukončené hodnotou null národní prostředí  
  
 `textRange`  
 Rozsah text, pro kterou platí tato změna  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. Jinak vrátí hodnotu FALSE  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
