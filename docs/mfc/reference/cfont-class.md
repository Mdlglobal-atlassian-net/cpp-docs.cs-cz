---
title: "CFont – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
dev_langs: C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5431461c7c2cc33131f72f059edcfbd984eae5fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cfont-class"></a>CFont – třída
Zapouzdří písmo Windows zařízení grafické rozhraní (GDI) a poskytuje členské funkce pro manipulaci s písmo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|Vytvoří `CFont` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFont::CreateFont](#createfont)|Inicializuje `CFont` s zadané vlastnosti.|  
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializuje `CFont` objekt s znaky uvedené v `LOGFONT` struktury.|  
|[CFont::CreatePointFont](#createpointfont)|Inicializuje `CFont` s zadaný výška měřená v desetin bodu a řezu písma.|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Stejné jako `CreateFontIndirect` s tím rozdílem, že výška písma se měří v desetin bod místo logické jednotky.|  
|[CFont::FromHandle](#fromhandle)|Vrátí ukazatel `CFont` objektu při zadané Windows **HFONT**.|  
|[CFont::GetLogFont](#getlogfont)|Vyplní celé `LOGFONT` s informacemi o logické písmo připojené k `CFont` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFont::operator HFONT](#operator_hfont)|Vrátí popisovač písma Windows GDI připojené k `CFont` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CFont` objektu, vytvořit `CFont` objektu a k němu se připojí písmo Windows [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), nebo [CreatePointFontIndirect](#createpointfontindirect)a potom pomocí objektu členské funkce k manipulaci s písmo.  
  
 `CreatePointFont` a `CreatePointFontIndirect` funkce jsou často jednodušší než `CreateFont` nebo `CreateFontIndirect` vzhledem k tomu, že se provést převod k výšce písma z bodu velikostí pro logické jednotky automaticky.  
  
 Další informace o `CFont`, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cfont"></a>CFont::CFont  
 Vytvoří `CFont` objektu.  
  
```  
CFont();
```  
  
### <a name="remarks"></a>Poznámky  
 Výsledný objekt musí být inicializovaný s `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, nebo `CreatePointFontIndirect` před použitím.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>CFont::CreateFont  
 Inicializuje `CFont` objekt se zadanou vlastností.  
  
```  
BOOL CreateFont(
    int nHeight,  
    int nWidth,  
    int nEscapement,  
    int nOrientation,  
    int nWeight,  
    BYTE bItalic,  
    BYTE bUnderline,  
    BYTE cStrikeOut,  
    BYTE nCharSet,  
    BYTE nOutPrecision,  
    BYTE nClipPrecision,  
    BYTE nQuality,  
    BYTE nPitchAndFamily,  
    LPCTSTR lpszFacename);
```  
  
### <a name="parameters"></a>Parametry  
 `nHeight`  
 Určuje požadovanou výšku (v logických jednotek) písma. Najdete v článku `lfHeight` členem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)struktura ve Windows SDK pro popis. Absolutní hodnota `nHeight` nesmí být delší než 16 384 jednotky zařízení po převedení. Pro všechny výška porovnání mapper písma hledá největší písma, které není delší než požadovaná velikost nebo jeho nejmenší Pokud všechna písma přesahují požadovanou velikost.  
  
 `nWidth`  
 Určuje průměrnou šířku (v logických jednotek) znaků v písmu k dispozici. Pokud `nWidth` je 0, poměr stran zařízení bude porovnání poměr stran digitization dostupných písem najít nejbližší odpovídající, což je dáno absolutní hodnotu rozdíl.  
  
 `nEscapement`  
 Určuje úhel (ve jednotky stupeň 0,1) mezi vektoru escapement a osy x zobrazení plochy. Vektor escapement je řádku prostřednictvím zdroje první a poslední znak na řádek. Úhel měří proti směru hodinových ručiček od osy x. Najdete v článku `lfEscapement` člena v `LOGFONT` struktura ve Windows SDK pro další informace.  
  
 `nOrientation`  
 Určuje úhel (ve jednotky stupeň 0,1) mezi základní znaku a osy x. Úhel měří proti směru hodinových ručiček od osy x pro systém souřadnic, ve kterých je směru osy y po směru hodinových ručiček osy x pro systém souřadnic, ve kterých je směru osy y nahoru a dolů.  
  
 `nWeight`  
 Určuje tloušťku písma (v pixelech propojeno na 1000). Najdete v článku `lfWeight` člena v `LOGFONT` struktura ve Windows SDK pro další informace. Popisuje hodnoty jsou jen přibližné; skutečný vzhled závisí na řezu písma. Některá písma mají jenom `FW_NORMAL`, `FW_REGULAR`, a `FW_BOLD` váhu. Pokud `FW_DONTCARE` je zadán, se používá výchozí váhu.  
  
 `bItalic`  
 Určuje, zda je písmo kurzíva.  
  
 `bUnderline`  
 Určuje, zda je podtržený písmo.  
  
 `cStrikeOut`  
 Určuje, zda jsou dopadu znaků v písmu k dispozici. Určuje písmo, přeškrtnutí Pokud nastavena na nenulovou hodnotu.  
  
 `nCharSet`  
 Určuje setSee znak písma `lfCharSet` člena v `LOGFONT` struktura ve Windows SDK pro seznam hodnot.  
  
 Znaková sada OEM je závislá na systému.  
  
 Písma s další znakových sad, můžou existovat v systému. Aplikace, která používá písmo s sadou Neznámý znak nesmí pokusí přeložit nebo interpretace řetězce, které mají být vykreslen s toto písmo. Místo toho řetězce by měla být předána přímo výstup ovladače zařízení.  
  
 Mapovač písma nepoužívá `DEFAULT_CHARSET` hodnotu. Aplikace můžete použít tuto hodnotu umožňuje název a velikost písma pro plně popis logické písmo. Pokud písmo se zadaným názvem neexistuje, písmo z jakékoli znakovou sadu můžete nahradit určeného písma. Chcete-li se vyhnout neočekávaným výsledkům, aplikace by měly používat `DEFAULT_CHARSET` pouze hodnotu.  
  
 `nOutPrecision`  
 Určuje požadovaný výstupní přesnost. Přesnost výstupu definuje, jak blízko výstup musí odpovídat požadované písmo výška, šířka, orientaci znak, escapement a výšku. Najdete v článku `lfOutPrecision` člena v `LOGFONT` struktura ve Windows SDK pro seznam hodnot a další informace.  
  
 `nClipPrecision`  
 Určuje požadovanou výstřižek přesnost. Přesnost výstřižek definuje, jak oříznutí znaků, které jsou částečně mimo oblast ořezu. Najdete v článku `lfClipPrecision` člena v `LOGFONT` struktura ve Windows SDK pro seznam hodnot.  
  
 Chcete-li použít vložené písmo jen pro čtení, musíte zadat aplikaci `CLIP_ENCAPSULATE`.  
  
 K dosažení konzistentní oběh zařízení, TrueType a vektorová písma, aplikace můžete použít operátor OR kombinovat `CLIP_LH_ANGLES` hodnotu s žádným z dalších `nClipPrecision` hodnoty. Pokud `CLIP_LH_ANGLES` je nastaven bit, otočení všechny písem závisí na tom, jestli je levou orientaci souřadnicový systém nebo pravou rukou. (Další informace o orientaci souřadnicových systémů, najdete v části Popis `nOrientation` parametru.) Pokud `CLIP_LH_ANGLES` není nastavený, písma zařízení vždy Otočit proti směru hodinových ručiček, ale je oběh jiná písma je závislá na orientaci souřadnicový systém.  
  
 `nQuality`  
 Určuje kvalitu výstupu písma, který definuje, jak pečlivě musí rozhraní GDI pokusí přiřadit logické písma atributy, které se u skutečné fyzické písma. Najdete v článku `lfQuality` člena v `LOGFONT` struktura ve Windows SDK pro seznam hodnot.  
  
 `nPitchAndFamily`  
 Určuje výšku a řadu písmo. Najdete v článku `lfPitchAndFamily` člena v `LOGFONT` struktura ve Windows SDK pro seznam hodnot a další informace.  
  
 `lpszFacename`  
 A `CString` nebo ukazatel na řetězec ukončené hodnotou null, který určuje název písma písma. Délka tento řetězec nesmí být delší než 30 znaků. Windows [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619) funkce slouží k zobrazení výčtu všechny aktuálně k dispozici písem. Pokud `lpszFacename` je `NULL`, používá rozhraní GDI řez písma nezávislé na zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Písmo lze následně vybrat jako písmo pro jakýkoli kontext zařízení.  
  
 `CreateFont` Funkce nevytvoří nové písmo GDI systému Windows. Vybere jenom nejbližší odpovídající z fyzického písem, která je k dispozici pro rozhraní GDI.  
  
 Aplikace můžete použít výchozí nastavení pro většinu parametrů při vytváření logické písmo. Parametry, které by měly být vždy uvedeny konkrétní hodnoty jsou `nHeight` a `lpszFacename`. Pokud `nHeight` a `lpszFacename` nejsou nastaveny aplikací, je logický písma, který se vytvoří závislé na zařízení.  
  
 Po dokončení se `CFont` objekt vytvořený `CreateFont` fungovat, použijte `CDC::SelectObject` Pokud chcete vybrat jiné písmo do kontextu zařízení, pak odstraňte `CFont` objekt, který již není potřeba.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>CFont::CreateFontIndirect  
 Inicializuje `CFont` objekt s znaky uvedené v [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)struktury.  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogFont`  
 Odkazuje na `LOGFONT` struktura, která určuje charakteristiky logické písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Písmo lze následně vybrat jako aktuální písma u všech zařízení.  
  
 Toto písmo má vlastností podle [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury. Pokud je vybrána písma s použitím [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) – členská funkce mapper písma GDI se pokusí o porovnání logické písmo existující fyzické písmem. Pokud mapper písma se nepodaří najít přesnou shodu pro logické písmo, poskytuje alternativní písma, jejichž vlastnosti odpovídají jako mnoho společných vlastností s požadovanou nejblíže.  
  
 Pokud již nepotřebujete `CFont` objekt vytvořený `CreateFontIndirect` fungovat, použijte `CDC::SelectObject` Pokud chcete vybrat jiné písmo do kontextu zařízení, pak odstraňte `CFont` objekt, který již není potřeba.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>CFont::CreatePointFont  
 Tato funkce poskytuje jednoduchý způsob, jak vytvořit písma pro zadaný řez písma a velikost bodu.  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nPointSize`  
 Požadovanou výšku písma v desetin bodu. (Například předejte 120 požádat o 12 bodů písma.)  
  
 `lpszFaceName`  
 A `CString` nebo ukazatel na řetězec ukončené hodnotou null, který určuje název písma písma. Délka tento řetězec nesmí být delší než 30 znaků. Windows **EnumFontFamilies** funkce slouží k zobrazení výčtu všechny aktuálně k dispozici písem. Pokud `lpszFaceName` je **NULL**, používá rozhraní GDI řez písma nezávislé na zařízení.  
  
 `pDC`  
 Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, který chcete použít k převedení výšku v `nPointSize` na logické jednotky. Pokud **NULL**, kontextu zařízení obrazovky se používá pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Převede ji automaticky výšku v `nPointSize` do logických jednotek pomocí `CDC` objektu na kterou odkazuje `pDC`.  
  
 Po dokončení se `CFont` objekt vytvořený `CreatePointFont` fungovat, nejprve vyberte písmo mimo kontext zařízení a pak odstraňte `CFont` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect  
 Tato funkce je stejný jako [CreateFontIndirect](#createfontindirect) s tím rozdílem, že **lfHeight** členem `LOGFONT` interpretována v desetin bodu spíše než zařízení jednotek.  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogFont`  
 Odkazuje na [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktura, která určuje charakteristiky logické písma. **LfHeight** členem `LOGFONT` struktura se měří v desetin bod místo logické jednotky. (Například nastavit **lfHeight** 120 požádat o 12 bodů písma.)  
  
 `pDC`  
 Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, který chcete použít k převedení výšku v **lfHeight** na logické jednotky. Pokud **NULL**, kontextu zařízení obrazovky se používá pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce automaticky převede výšku v **lfHeight** do logických jednotek pomocí `CDC` objektu na kterou odkazuje `pDC` před předávání `LOGFONT` struktura k systému Windows.  
  
 Po dokončení se `CFont` objekt vytvořený `CreatePointFontIndirect` fungovat, nejprve vyberte písmo mimo kontext zařízení a pak odstraňte `CFont` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CFont::FromHandle  
 Vrátí ukazatel na `CFont` objektu při zadané **HFONT** zpracování na objekt písma GDI systému Windows.  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>Parametry  
 `hFont`  
 **HFONT** popisovač písmo Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CFont` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CFont` objekt není už připojený k popisovač dočasného `CFont` objekt se vytvoří a připojené. Toto dočasný `CFont` je objekt platný pouze dokud příště aplikace má čas nečinnosti v jeho událostí smyčky, na který čas všechny dočasné obrázek objekty jsou odstraněny. Jinými slovy to je, že dočasný objekt je platný pouze při zpracování zprávy jeden interval.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>CFont::GetLogFont  
 Volání této funkce se načíst kopii `LOGFONT` struktury pro `CFont`.  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>Parametry  
 *pLogFont*  
 Ukazatel [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktura získat informace písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci úspěšné, jinak hodnota 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>CFont::operator HFONT  
 Použití tohoto operátoru získat popisovač Windows GDI písma připojené k `CFont` objektu.  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač objektu písma Windows GDI připojené k `CFont` li úspěšné, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Vzhledem k tomu tento operátor. je automaticky použita pro převody z `CFont` k [písma a Text](http://msdn.microsoft.com/library/windows/desktop/dd144819), můžete předat `CFont` objekty na funkce, které očekávají **HFONT**s.  
  
 Další informace o použití grafických objektů najdete v tématu [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



