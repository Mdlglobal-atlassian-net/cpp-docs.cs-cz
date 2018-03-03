---
title: Implementace modulu Plug-In architektury (C + +/ CLI) | Microsoft Docs
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
- plug-ins [C++]
- reflection [C++}, plug-ins
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 05c6c2584e39ed145a30c919ed850aac45905a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-implement-a-plug-in-component-architecture-using-reflection-ccli"></a>Postupy: Implementace architektury komponenty modulu plugin pomocí reflexe (C++/CLI)
Následující příklady kódu ukazují použití reflexe k implementaci jednoduché architektury "plug-in". První odkaz je aplikace, a druhá je modul plug-in. Aplikace je několik dokumentů formulář, který naplní samotné pomocí všechny nalezené v knihovnu DLL modulu plug-in zadaný jako argument příkazového řádku založené na formulářích třídy.  
  
 Aplikace se pokusí načíst zadané sestavení pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> metoda. Pokud úspěšné, typy v sestavení jsou uvedené pomocí <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> metoda. Každý typ je pak kontrola kompatibility pomocí <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> metoda. V tomto příkladu musí být odvozen od třídy v zadané sestavení <xref:System.Windows.Forms.Form> třídy pro kvalifikaci jako modul plug-in.  
  
 Potom instance třídy kompatibilní s <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> metodu, která přijímá <xref:System.Type> jako argument a vrací ukazatel na novou instanci. Každé nové instance je pak připojený do formuláře a zobrazí.  
  
 Všimněte si, že <xref:System.Reflection.Assembly.Load%2A> metoda nepřijímá názvy sestavení, které mají příponu souboru. Hlavní funkce v aplikaci ořízne všechny zadané přípony, takže následující příklad kódu funguje v obou případech.  
  
## <a name="example"></a>Příklad  
 Následující kód definuje aplikaci, která přijímá moduly plug-in. Jako první argument musí být zadán název sestavení. Toto sestavení by měl obsahovat alespoň jeden veřejný <xref:System.Windows.Forms.Form> odvozeného typu.  
  
```  
// plugin_application.cpp  
// compile with: /clr /c  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
  
ref class PluggableForm : public Form  {  
public:  
   PluggableForm() {}  
   PluggableForm(Assembly^ plugAssembly) {  
      Text = "plug-in example";  
      Size = Drawing::Size(400, 400);  
      IsMdiContainer = true;  
  
      array<Type^>^ types = plugAssembly->GetTypes( );  
      Type^ formType = Form::typeid;  
  
      for (int i = 0 ; i < types->Length ; i++) {  
         if (formType->IsAssignableFrom(types[i])) {  
            // Create an instance given the type description.  
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));  
            if (f) {  
               f->Text = types[i]->ToString();  
               f->MdiParent = this;  
               f->Show();  
            }  
         }  
      }  
   }  
};  
  
int main() {  
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");  
   Application::Run(gcnew PluggableForm(a));  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující kód definuje tři třídy odvozené od třídy <xref:System.Windows.Forms.Form>. Pokud název výsledný název sestavení je předán spustitelný soubor v předchozí ukázce, každá z těchto tří tříd, se zjistí a vytvoření instance přes skutečnost, že byly všechny neznámé hostitelskou aplikaci v době kompilace.  
  
```  
// plugin_assembly.cpp  
// compile with: /clr /LD  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
using namespace System::Drawing;  
  
public ref class BlueForm : public Form {  
public:  
   BlueForm() {  
      BackColor = Color::Blue;  
   }  
};  
  
public ref class CircleForm : public Form {  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);  
   }  
};  
  
public ref class StarburstForm : public Form {  
public:  
   StarburstForm(){  
      BackColor = Color::Black;  
   }  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      Pen^ p = gcnew Pen(Color::Red, 2);  
      Random^ r = gcnew Random( );  
      Int32 w = ClientSize.Width;  
      Int32 h = ClientSize.Height;  
      for (int i=0; i<100; i++) {  
         float x1 = w / 2;  
         float y1 = h / 2;  
         float x2 = r->Next(w);  
         float y2 = r->Next(h);  
         args->Graphics->DrawLine(p, x1, y1, x2, y2);  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Reflexe (C++/CLI)](../dotnet/reflection-cpp-cli.md)