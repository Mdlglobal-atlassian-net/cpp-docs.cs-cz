---
title: "Rutiny ověřování dat standardního dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33566bcdfab1a618dc8ff79deb375b3f9d1221f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="standard-dialog-data-validation-routines"></a>Rutiny ověřování dat standardního dialogového okna
Toto téma uvádí rutiny ověření (DDV) dat standardního dialogového okna použít pro běžné ovládací prvky MFC dialogové okno.  
  
> [!NOTE]
>  Rutiny výměny dat standardního dialogového okna jsou definovány v afxdd_.h soubor hlavičky. Aplikace by měla obsahovat však afxwin.h.  
  
### <a name="ddv-functions"></a>DDV funkce  
  
|||  
|-|-|  
|[Ddv_maxchars –](#ddv_maxchars)|Ověřuje, že počet znaků hodnoty daný ovládací prvek není delší než daný maximální.|  
|[Ddv_minmaxbyte –](#ddv_minmaxbyte)|Ověřuje, není větší než hodnota daný ovládací prvek danou **BAJTŮ** rozsahu.|  
|[Ddv_minmaxdatetime –](#ddv_minmaxdatetime)|Ověřuje, že daný ovládací prvek hodnotu nepřekročí za dané časové období.|  
|[Ddv_minmaxdouble –](#ddv_minmaxdouble)|Ověřuje, není větší než hodnota daný ovládací prvek danou **dvojité** rozsahu.|  
|[Ddv_minmaxdword –](#ddv_minmaxdword)|Ověřuje, není větší než hodnota daný ovládací prvek danou **DWORD** rozsahu.|  
|[Ddv_minmaxfloat –](#ddv_minmaxfloat)|Ověřuje, není větší než hodnota daný ovládací prvek danou **float** rozsahu.|  
|[Ddv_minmaxint –](#ddv_minmaxint)|Ověřuje, není větší než hodnota daný ovládací prvek danou **int** rozsahu.|  
|[Ddv_minmaxlong –](#ddv_minmaxlong)|Ověřuje, není větší než hodnota daný ovládací prvek danou **dlouho** rozsah.|  
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Ověřuje, není větší než hodnota daný ovládací prvek danou **LONGLONG** rozsahu.|  
|[Ddv_minmaxmonth –](#ddv_minmaxmonth)|Ověřuje, že daný ovládací prvek hodnota než v daném období.|  
|[DDV_MinMaxShort](#ddv_minmaxshort)|Ověřuje, není větší než hodnota daný ovládací prvek danou **krátké** rozsahu.|  
|[Ddv_minmaxslider –](#ddv_minmaxslider)|Ověřuje, že hodnotu ovládacího prvku posuvník dané spadá do daného rozsahu.|  
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Ověřuje, není větší než hodnota daný ovládací prvek danou **Celé_číslo** rozsahu.|  
|[Ddv_minmaxunsigned –](#ddv_minmaxuint)|Ověřuje, že daný ovládací prvek hodnotu leží mezi dvěma zadanými hodnotami.| 
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Ověřuje, není větší než hodnota daný ovládací prvek danou **ULONGLONG** rozsahu.|  
  

  
##  <a name="ddv_maxchars"></a>Ddv_maxchars –  
 Volání `DDV_MaxChars` k ověření, že počet znaků v ovládacím prvku přidružené *hodnotu* není delší než *nChars*.  
  
```   
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,  
    CString const& value,  
    int nChars); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `nChars`  
 Maximální povolený počet znaků.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxbyte"></a>Ddv_minmaxbyte –  
 Volání `DDV_MinMaxByte` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,  
    BYTE value,  
    BYTE minVal,  
    BYTE maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **BAJTŮ**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **BAJTŮ**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxdatetime"></a>Ddv_minmaxdatetime –  
 Volání `DDV_MinMaxDateTime` k ověření, že ovládacích prvků hodnota času a data v dialogu pro výběr data a času ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) přidružené k *refValue* leží mezi `refMinRange` a `refMaxRange`.  
  
```   
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,  
    CTime& refValue,  
    const CTime* refMinRange,  
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,  
    COleDateTime& refValue,  
    const COleDateTime* refMinRange,  
    const COleDateTime* refMaxRange); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr. Nemusíte odstranit tento objekt.  
  
 *refValue*  
 Odkaz na [CTime –](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt přidružený k členské proměnné dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku. Tento objekt obsahuje data, která mají být ověřen.  
  
 `refMinRange`  
 Minimální povolená hodnota data a času.  
  
 `refMaxRange`  
 Datum a čas maximální povolená hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxdouble"></a>Ddv_minmaxdouble –  
 Volání `DDV_MinMaxDouble` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,  
    double const& value,  
    double minVal,  
    double maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **dvojité**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **dvojité**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxdword"></a>Ddv_minmaxdword –  
 Volání `DDV_MinMaxDWord` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,  
    DWORD const& value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu `DWORD`) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu `DWORD`) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxfloat"></a>Ddv_minmaxfloat –  
 Volání `DDV_MinMaxFloat` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,  
    float value,  
    float minVal,  
    float maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **float**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **float**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxint"></a>Ddv_minmaxint –  
 Volání `DDV_MinMaxInt` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,  
    int value,  
    int minVal,  
    int maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu `int`) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu `int`) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxlong"></a>Ddv_minmaxlong –  
 Volání `DDV_MinMaxLong` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,  
    long value,  
    long minVal,  
    long maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **dlouho**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **dlouho**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong  
 Volání `DDV_MinMaxLongLong` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,  
    LONGLONG value,  
    LONGLONG minVal,  
    LONGLONG maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **LONGLONG**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **LONGLONG**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxmonth"></a>Ddv_minmaxmonth –  
 Volání `DDV_MinMaxMonth` k ověření, že řízení hodnotě času a data v měsíční kalendář ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) přidružené k *refValue* leží mezi `refMinRange` a `refMaxRange`.  
  
```   
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,  
    CTime& refValue,  
    const CTime* refMinRange,  
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,  
    COleDateTime& refValue,  
    const COleDateTime* refMinRange,  
    const COleDateTime* refMaxRange); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *refValue*  
 Odkaz na objekt typu `CTime` nebo `COleDateTime` přidružené členské proměnné dialogového okna, zobrazení formuláře nebo řídit objekt zobrazení. Tento objekt obsahuje data, která mají být ověřen. MFC předává to odkazovat při `DDV_MinMaxMonth` je volána.  
  
 `refMinRange`  
 Minimální povolená hodnota data a času.  
  
 `refMaxRange`  
 Datum a čas maximální povolená hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxshort"></a>DDV_MinMaxShort  
 Volání `DDV_MinMaxShort` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,  
    short value,  
    short minVal,  
    short maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **krátké**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **krátké**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxslider"></a>Ddv_minmaxslider –  
 Volání `DDV_MinMaxSlider` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,  
    DWORD value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na hodnota, která má být ověřen. Tento parametr obsahuje nebo nastaví ovládací prvek jezdec aktuální pozici jezdce.  
  
 `minVal`  
 Minimální povolená hodnota.  
  
 `maxVal`  
 Maximální povolená hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích posuvníku najdete v tématu [pomocí CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxuint"></a>DDV_MinMaxUInt  
 Volání `DDV_MinMaxUInt` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,  
    UINT value,  
    UINT minVal,  
    UINT maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **Celé_číslo**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **Celé_číslo**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong  
 Volání `DDV_MinMaxULongLong` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,  
    ULONGLONG value,  
    ULONGLONG  minVal ,  
    ULONGLONG  maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **ULONGLONG**) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **ULONGLONG**) povolen.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
    
## <a name="see-also"></a>Viz také  
 [Rutiny výměny dat standardního dialogového okna](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)

 ## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned
Volání `DDV_MinMaxUnsigned` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi `minVal` a `maxVal`.  
   
### <a name="syntax"></a>Syntaxe    
```
   void AFXAPI DDV_MinMaxUnsigned(  
       CDataExchange* pDX,  
       unsigned value,  
       unsigned minVal,  
       unsigned maxVal );  
```
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, se kterým je ověřit data.  
  
 `minVal`  
 Minimální hodnota (typu **nepodepsané** ) povolen.  
  
 `maxVal`  
 Maximální hodnota (typu **nepodepsané** ) povolen.  
   
### <a name="remarks"></a>Poznámky  
 Další informace o DDV najdete v tématu [výměna dialogových dat a ověření](../dialog-data-exchange-and-validation.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdd_.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [Ddx_slider –](#ddx_slider)   
 [Ddx_fieldslider –](#ddx_fieldslider)
 


