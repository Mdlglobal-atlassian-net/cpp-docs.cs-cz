---
title: "Agregace a třída objektu pro vytváření makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
dev_langs: C++
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d18afdfe08a97a7a685b373b1f8951799836ab1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="aggregation-and-class-factory-macros"></a>Agregace a makra objekt pro vytváření tříd
Tyto makra nabízejí způsoby řízení agregace a deklarování tříd.  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, že vaše objekt může být agregován (výchozí).|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje objektu pro vytváření tříd jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ATL výchozí třídy objekt pro vytváření.|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje objektu factory třída objektu pro vytváření tříd.|  
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako objekt pro vytváření tříd.|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd.|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako objekt pro vytváření tříd.|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje virtuální `GetControllingUnknown` funkce.|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, že objektu nemůže být agregován.|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, že musí být agregován objektu.|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Ověří, hodnota vnější neznámý a deklaruje objektu agregovatelné nebo neagregovatelný, podle potřeby.|  
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Objekt vnější chrání před odstraněním během vytváření vnitřní objekt.|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|Určuje, **stavu** příznaky do kontejneru.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
   
##  <a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE  
 Určuje, že se dají agregovat objektu.  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název třídy, kterou definujete jako agregovatelné.  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje tento makro zadat výchozí agregace model. Pokud chcete přepsat toto výchozí nastavení, zadejte buď [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) nebo [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) makra v definici vaší třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_classfactory"></a>DECLARE_CLASSFACTORY  
 Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) používá tento makro deklarovat výchozí objekt factory třídy pro objekt.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="ccomclassfactory_class"></a>CComClassFactory – třída  
 Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní.  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Poznámky  
 `CComClassFactory`implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní, která obsahuje metody pro vytvoření objektu konkrétní CLSID, jakož i zámek objektu pro vytváření tříd v paměti umožňuje rychleji vytvořit nové objekty. **IClassFactory** pro každou třídu, která zaregistrujete v registru systému a můžete přiřadit identifikátor CLSID, musí být implementována.  
  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li přepsat toto výchozí nastavení, zadejte jednu z `DECLARE_CLASSFACTORY` *XXX* makra v definici vaší třídy. Například [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) makro používá pro zadanou třídu objektu pro vytváření tříd:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 Výše uvedené definice třídy určuje, že **CMyClassFactory** se použije jako zdroj tříd výchozí objektu. **CMyClassFactory** musí být odvozeny od `CComClassFactory` a přepsání `CreateInstance`.  
  
 ATL poskytuje tři makra s objekt třídy:  
  
- [DECLARE_CLASSFACTORY2](#declare_classfactory2) používá [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), který řídí vytváření prostřednictvím licenci.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) používá [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), která vytvoří objekty v několika Apartment.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) používá [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), který vytvoří jeden [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objektu.  
  
##  <a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX  
 Deklaruje `cf` jako objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 [v] Název třídy, která implementuje objekt factory vaší třídy.  
  
### <a name="remarks"></a>Poznámky  
 `cf` Parametr musí být odvozeny od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a přepsat `CreateInstance` metoda.  
  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, který určuje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Ale zahrnutím `DECLARE_CLASSFACTORY_EX` makra v definici třídy objektu, můžete přepsat toto výchozí nastavení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2  
 Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>Parametry  
 *– Licenční smlouva*  
 [v] Třídu, která implementuje `VerifyLicenseKey`, `GetLicenseKey`, a `IsLicenseValid`.  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, který určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Ale zahrnutím `DECLARE_CLASSFACTORY2` makra v definici třídy objektu, můžete přepsat toto výchozí nastavení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="ccomclassfactory2_class"></a>CComClassFactory2 – třída  
 Tato třída implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní.  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>Parametry  
 *licence*  
 Třídu, která implementuje statické následující funkce:  
  
- **verifylicensekey – statické BOOL (BSTR** `bstr` **);**  
  
- **getlicensekey – statické BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **statické BOOL IsLicenseValid ();**  
  
### <a name="remarks"></a>Poznámky  
 `CComClassFactory2`implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní, což je rozšíření z [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** ovládací prvky objektu vytváření licence. Spuštění licenční klíč můžete zadat třídu objektu pro vytváření, provádění na licencovanou počítači. Tento licenční klíč umožňuje aplikaci k vytváření instancí objektů při úplné počítač licence neexistuje.  
  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactory2`, zadejte [DECLARE_CLASSFACTORY2](#declare_classfactory2) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 **CMyLicense**, parametr šablony k `CComClassFactory2`, musí implementovat statické funkce `VerifyLicenseKey`, `GetLicenseKey`, a `IsLicenseValid`. Následuje příklad jednoduchého licence třídy:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2`je odvozena z obou **CComClassFactory2Base** a *licence*. **CComClassFactory2Base**, pak je odvozena z **IClassFactory2** a **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
##  <a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD  
 Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, který určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Ale zahrnutím `DECLARE_CLASSFACTORY_AUTO_THREAD` makra v definici třídy objektu, můžete přepsat toto výchozí nastavení.  
  
 Při vytváření objektů v několika apartment (v serveru out-of-proc), přidejte `DECLARE_CLASSFACTORY_AUTO_THREAD` na třídu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="ccomclassfactoryautothread_class"></a>CComClassFactoryAutoThread – třída  
 Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní a umožňuje vytvořit v několika Apartment objekty.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Poznámky  
 `CComClassFactoryAutoThread`je podobná [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umožňuje vytvořit v několika Apartment objekty. Abyste mohli využívat této podpory, odvozena EXE modul z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactoryAutoThread`, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON  
 Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>Parametry  
 `obj`  
 [v] Název třídy objektu.  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, který určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Ale zahrnutím `DECLARE_CLASSFACTORY_SINGLETON` makra v definici třídy objektu, můžete přepsat toto výchozí nastavení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="ccomclassfactorysingleton_class"></a>CComClassFactorySingleton – třída  
 Tato třída odvozená z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy.  
  
 `CComClassFactorySingleton`odvozená z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metoda jednoduše dotazuje tohoto objektu pro ukazatele rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactorySingleton`, zadejte [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN  
 Deklaruje virtuální funkci `GetControllingUnknown`.  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>Poznámky  
 Přidání této makro do objektu, pokud získání chybové zprávy kompilátoru `GetControllingUnknown` není definován (například v **CComAggregateCreator**).  
  
##  <a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE  
 Určuje, že objektu nemůže být agregován.  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název objektu třídy, kterou definujete jako neagregovatelný.  
  
### <a name="remarks"></a>Poznámky  
 `DECLARE_NOT_AGGREGATABLE`způsobí, že `CreateInstance` vrátit chybu ( **CLASS_E_NOAGGREGATION**) Pokud je proveden pokus o k agregaci do objektu.  
  
 Ve výchozím nastavení [CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_AGGREGATABLE](#declare_aggregatable) makro, která určuje, že se dají agregovat objektu. Chcete-li přepsat toto výchozí chování, zahrňte `DECLARE_NOT_AGGREGATABLE` v definici vaší třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE  
 Určuje, že musí být agregován objektu.  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název objektu třídy, kterou definujete jako pouze agregovatelné.  
  
### <a name="remarks"></a>Poznámky  
 `DECLARE_ONLY_AGGREGATABLE`Výsledkem bude chyba ( **E_FAIL**) Pokud je proveden pokus o **CoCreate** objektu jako neagregovaná objekt.  
  
 Ve výchozím nastavení [CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_AGGREGATABLE](#declare_aggregatable) makro, která určuje, že se dají agregovat objektu. Chcete-li přepsat toto výchozí chování, zahrňte `DECLARE_ONLY_AGGREGATABLE` v definici vaší třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE  
 Určuje, že instance **CComPolyObject \<**  *x*  **>**  se vytvoří při vytvoření objektu.  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název objektu třídy, kterou definujete jako agregovatelné nebo neagregovatelný.  
  
### <a name="remarks"></a>Poznámky  
 Během vytváření se kontroluje hodnota vnější neznámý. Pokud je **NULL**, **IUnknown** je implementována pro objekt neagregovaná. Pokud vnější Neznámý není **NULL**, **IUnknown** je implementována pro agregovaný objekt.  
  
 Výhodou použití `DECLARE_POLY_AGGREGATABLE` je vyhnout se nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případy. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že pouze jedna kopie tabulce vtable a jednu kopii funkce existují v modulu. Pokud vaše vtable velká, může to podstatně snížit velikost vašeho modulu. Ale pokud je vaše vtable malá, pomocí `CComPolyObject` může způsobit něco větší velikost modulu, protože není optimalizována pro agregovaná nebo neagregovaná objekt, jako jsou `CComAggObject` a `CComObject`.  
  
 `DECLARE_POLY_AGGREGATABLE` Makro je automaticky deklarován v objektu, pokud použijete Průvodce ovládacím prvkem ATL k vytvoření úplné řízení.  
  
##  <a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT  

 Chrání před odstraněním Pokud objektu (během [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) interní agregovaný objekt zvětší počet odkazů a snižuje počet na hodnotu 0.  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="declare_view_status"></a>DECLARE_VIEW_STATUS  
 Umístit tento makro ovládacího prvku ActiveX knihovny ATL třída ovládacích prvků k určení **stavu** příznaky do kontejneru.  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>Parametry  
 `statusFlags`  
 [v] **Stavu** příznaky. V tématu [stavu](http://msdn.microsoft.com/library/windows/desktop/ms687201) seznam příznaky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
