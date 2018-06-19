---
title: CMetaFileDC – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a588a848e7964a70f47d4cf29a5f5ef2741881d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368144"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC – třída
Implementuje WMF, který obsahuje posloupnost grafiky zařízení rozhraní GDI příkazy, které můžete přehráním vytvořit požadovanou image nebo text.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Vytvoří `CMetaFileDC` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|Zavře kontextu zařízení a vytvoří metafile popisovač.|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Zavře kontextu zařízení enhanced metafile a vytvoří popisovač enhanced metafile.|  
|[CMetaFileDC::Create](#create)|Kontext zařízení Windows metafile vytvoří a připojí jej k `CMetaFileDC` objektu.|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Vytvoří metafile kontextu zařízení pro metafile rozšířeného formátu.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li implementovat WMF, nejprve vytvořit `CMetaFileDC` objektu. Vyvolání `CMetaFileDC` konstruktoru, potom zavolejte [vytvořit](#create) členská funkce, který vytvoří kontextu zařízení Windows metafile a připojí jej k `CMetaFileDC` objektu.  
  
 Potom pošle `CMetaFileDC` objektu pořadí `CDC` GDI příkazy, které chcete pro něj opakování. Pouze GDI příkazy, které vytvoření výstupu, jako například `MoveTo` a `LineTo`, můžete použít.  
  
 Po odeslání požadované příkazy metafile volání **Zavřít** členská funkce, která zavře kontexty zařízení metafile a vrátí popisovač metafile. Pak odstranění `CMetaFileDC` objektu.  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) lze následně použít popisovač metafile k opakované přehrávání metafile. Metafile můžete manipulovat rovněž prostřednictvím funkce systému Windows, jako [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480), který zkopíruje metasoubory na disk.  
  
 Když metafile již nepotřebujete, odstraňte jej z paměti s [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) funkce systému Windows.  
  
 Můžete taky implementovat `CMetaFileDC` objektu tak, aby dokáže zpracovat výstup volání i atribut GDI volání, jako `GetTextExtent`. Takové metafile je flexibilnější a můžete více snadno opakovaně použít obecné GDI kód, který často se skládá z kombinace výstup a atribut volání. `CMetaFileDC` Třída dědí dva kontexty zařízení `m_hDC` a `m_hAttribDC`, z `CDC`. `m_hDC` Kontextu zařízení zpracovává všechny [CDC](../../mfc/reference/cdc-class.md) GDI výstup volání a `m_hAttribDC` kontextu zařízení zpracovává všechny `CDC` GDI atribut volání. Za normálních okolností kontexty tyto dvě zařízení odkazovat na stejné zařízení. U `CMetaFileDC`, atribut řadič domény je nastaven na **NULL** ve výchozím nastavení.  
  
 Vytvořte druhý kontextu zařízení, které odkazuje na obrazovce, tiskárnu nebo zařízení než metasoubory, pak volat `SetAttribDC` – členská funkce přidružit nový kontext zařízení s `m_hAttribDC`. Volání GDI informace teď budou směrovány do nového `m_hAttribDC`. Výstup GDI volání přejde na `m_hDC`, která představuje metafile.  
  
 Další informace o `CMetaFileDC`, najdete v části [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="close"></a>  CMetaFileDC::Close  
 Zavře kontextu zařízení metafile a vytvoří popisovačů metafile systému Windows, který slouží k přehrávání metafile pomocí [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) – členská funkce.  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Platná **HMETAFILE** Pokud je funkce úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač metafile Windows můžete také použít k manipulaci metafile s funkcemi Windows, jako [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480).  
  
 Odstranit metafile po použití voláním Windows [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) funkce.  
  
##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced  
 Zavře kontextu zařízení enhanced metafile a vrátí popisovač, který identifikuje metafile rozšířeného formátu.  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač EMF, v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace můžete použít enhanced metafile popisovač vrácený tuto funkci k provádění následujících úloh:  
  
-   Zobrazení uložené v EMF obrázku  
  
-   Vytvořit kopie EMF  
  
-   Zobrazení výčtu, upravit nebo zkopírovat jednotlivé záznamy v rozšířené metafile  
  
-   Načtení volitelný popis metafile obsahu z hlavičky enhanced metafile  
  
-   Načtení kopie EMF – hlavička  
  
-   Načtení binární kopie EMF  
  
-   Zobrazení výčtu barev v volitelné palety  
  
-   Převést do formátu Windows metafile metafile rozšířeného formátu  
  
 Pokud aplikace již nepotřebuje EMF popisovač, ho měli uvolnit popisovač voláním Win32 **DeleteEnhMetaFile** funkce.  
  
##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC  
 Vytvořit `CMetaFileDC` objektu ve dvou krocích.  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>Poznámky  
 Nejprve volání `CMetaFileDC`, pak zavolají **vytvořit**, která vytvoří kontext Windows metafile zařízení a připojí jej k `CMetaFileDC` objektu.  
  
##  <a name="create"></a>  CMetaFileDC::Create  
 Vytvořit `CMetaFileDC` objektu ve dvou krocích.  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFilename*  
 Odkazuje na řetězec znaků ukončený hodnotou null. Určuje název souboru metafile vytvořit. Pokud *lpszFilename* je **NULL**, se vytvoří nový metafile v paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nejprve volat konstruktor `CMetaFileDC`, pak zavolají **vytvořit**, která vytvoří kontext Windows metafile zařízení a připojí jej k `CMetaFileDC` objektu.  
  
##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced  
 Vytvoří kontext zařízení pro metafile rozšířeného formátu.  
  
```  
BOOL CreateEnhanced(
    CDC* pDCRef,  
    LPCTSTR lpszFileName,  
    LPCRECT lpBounds,  
    LPCTSTR lpszDescription);
```  
  
### <a name="parameters"></a>Parametry  
 `pDCRef`  
 Odkaz na zařízení, které EMF identifikuje.  
  
 `lpszFileName`  
 Odkazuje na řetězec znaků ukončený hodnotou null. Určuje název souboru pro EMF, který se má vytvořit. Pokud tento parametr je **NULL**, je EMF paměti na základě a její obsah ztráty při zničena objektu nebo při Win32 **DeleteEnhMetaFile** funkce je volána.  
  
 `lpBounds`  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura dat nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje dimenze v **HIMETRIC** jednotek (v přírůstcích po.01 milimetru) na obrázku má být uložen v EMF.  
  
 `lpszDescription`  
 Bodů na nule ukončena řetězec, který určuje název aplikace, která vytvořila na obrázku, stejně jako nadpis na obrázku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení pro EMF, v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tento řadič domény můžete použít k uložení obrázku nezávislé na zařízení.  
  
 Odkaz na zařízení identifikovaný používá Windows `pDCRef` parametr k zaznamenání překlad IP adres a jednotky zařízení původně zobrazovaly obrázku. Pokud `pDCRef` parametr je **NULL**, používá aktuální zobrazovací zařízení pro referenci.  
  
 Členové levého a horního `RECT` struktura dat na kterou odkazuje `lpBounds` parametr musí být menší než členy vpravo a dole v uvedeném pořadí. Body podél okrajů obdélníku, jsou součástí na obrázku. Pokud `lpBounds` je **NULL**, rozhraní zařízení grafiky (GDI) vypočítá dimenze nejmenší obdélníku, který může zahrnout obrázek vykreslovat aplikací. `lpBounds` By měl být zadán parametr, kde je to možné.  
  
 Řetězec na kterou odkazuje `lpszDescription` parametr musí obsahovat znak hodnoty null mezi název aplikace a název obrázku a musí být ukončen s dva znaky null – například "XYZ grafiky Editor\0Bald Eagle\0\0," kde \0 představuje hodnotu null znak. Pokud `lpszDescription` je **NULL**, neexistuje žádný odpovídající záznam v hlavičce enhanced metafile.  
  
 Aplikace používat k ukládání grafiky obrázek ve formátu EMF řadič domény vytvořené pomocí této funkce. Všechny funkce GDI lze předat popisovač identifikující tento řadič domény.  
  
 Po aplikace ukládá obrázek ve formátu EMF, ho můžete zobrazit na jakéhokoli výstupu zařízení voláním `CDC::PlayMetaFile` funkce. Při zobrazení na obrázku, systém Windows používá obdélníku, na kterou odkazuje `lpBounds` parametr a řešení data ze zařízení odkaz pozice a škálovat na obrázku. Kontext zařízení, vrátí tato funkce obsahuje stejnou výchozí atributy přidružené žádné nový řadič domény.  
  
 Aplikace musí používat Win32 **GetWinMetaFileBits** funkce převést EMF starší formát WMF.  
  
 Název souboru pro rozšířené metafile měli používat. EMF rozšíření.  
  
## <a name="see-also"></a>Viz také  
 [Třída CDC](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



