---
title: Třída CD2DTextFormat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 017267a2b633ee8e0a9c23149fe9d3cb7a8be980
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955466"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat – třída
Obálka pro IDWriteTextFormat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Vytvoří objekt CD2DTextFormat.|  
|[CD2DTextFormat:: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|Destruktor. Voláno, když je zničen objektu D2D textového formátu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextFormat::Create](#create)|Vytvoří CD2DTextFormat. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextFormat::Destroy](#destroy)|Zničí CD2DTextFormat objektu. (Přepisuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextFormat::Get](#get)|Vrátí IDWriteTextFormat rozhraní|  
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Získá kopii název rodiny písem.|  
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Získá kopii název národního prostředí.|  
|[CD2DTextFormat::IsValid](#isvalid)|Ověří platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextFormat::ReCreate](#recreate)|Znovu vytvoří CD2DTextFormat. (Přepisuje [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextFormat::Operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Vrátí IDWriteTextFormat rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Ukazatel IDWriteTextFormat.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextformat"></a>  CD2DTextFormat:: ~ CD2DTextFormat  
 Destruktor. Voláno, když je zničen objektu D2D textového formátu.  
  
```  
virtual ~CD2DTextFormat();
```  
  
##  <a name="cd2dtextformat"></a>  CD2DTextFormat::CD2DTextFormat  
 Vytvoří objekt CD2DTextFormat.  
  
```  
CD2DTextFormat(
    CRenderTarget* pParentTarget,  
    const CString& strFontFamilyName,  
    FLOAT fontSize,  
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,  
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,  
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,  
    const CString& strFontLocale = _T(""),  
    IDWriteFontCollection* pFontCollection = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentTarget*  
 Ukazatel na cíl vykreslení.  
  
 *strFontFamilyName*  
 CString objekt, který obsahuje název rodiny písem.  
  
 *velikost písma*  
 Logická velikost písma v jednotkách vyhrazené IP adresy ("nezávislé na zařízení pixelů"). DIPequals 1/96 palce.  
  
 *Tloušťka písma*  
 Hodnota, která určuje váha písmo pro text objektu.  
  
 *fontStyle*  
 Hodnota, která určuje písmo pro text objektu.  
  
 *fontStretch*  
 Hodnota, která určuje stretch písmo pro text objektu.  
  
 *strFontLocale*  
 CString objekt, který obsahuje název národního prostředí.  
  
 *pFontCollection*  
 Ukazatel na objekt kolekce písma. Pokud je hodnota NULL, označuje kolekce písem systému.  
  
 *bAutoDestroy*  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>  CD2DTextFormat::Create  
 Vytvoří CD2DTextFormat.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>  CD2DTextFormat::Destroy  
 Zničí CD2DTextFormat objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>  CD2DTextFormat::Get  
 Vrátí IDWriteTextFormat rozhraní  
  
```  
IDWriteTextFormat* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IDWriteTextFormat nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getfontfamilyname"></a>  CD2DTextFormat::GetFontFamilyName  
 Získá kopii název rodiny písem.  
  
```  
CString GetFontFamilyName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 CString objekt, který obsahuje aktuální název rodiny písem.  
  
##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName  
 Získá kopii název národního prostředí.  
  
```  
CString GetLocaleName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 CString objekt, který obsahuje název aktuální národní prostředí.  
  
##  <a name="isvalid"></a>  CD2DTextFormat::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat  
 Ukazatel IDWriteTextFormat.  
  
```  
IDWriteTextFormat* m_pTextFormat;  
```  
  
##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::Operator IDWriteTextFormat *  
 Vrátí IDWriteTextFormat rozhraní  
  
```  
operator IDWriteTextFormat*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IDWriteTextFormat nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="recreate"></a>  CD2DTextFormat::ReCreate  
 Znovu vytvoří CD2DTextFormat.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
