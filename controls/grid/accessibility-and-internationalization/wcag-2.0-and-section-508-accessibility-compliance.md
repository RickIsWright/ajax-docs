---
title: WCAG 2.0 and Section 508 Accessibility Compliance
page_title: WCAG 2.0 and Section 508 Accessibility Compliance | RadGrid for ASP.NET AJAX Documentation
description: WCAG 2.0 and Section 508 Accessibility Compliance
slug: grid/accessibility-and-internationalization/wcag-2.0-and-section-508-accessibility-compliance
tags: wcag,2.0,and,section,508,accessibility,compliance
published: True
position: 8
---

# WCAG 2.0 and Section 508 Accessibility Compliance



## 

RadGrid for ASP.NET AJAX satisfies the requirements of "Section 508" for software accessibility, as well as thosefor level AA (in compliance with the W3C Web Accessibility Guidelines 2.0).

[This online example](https://demos.telerik.com/aspnet-ajax/grid/examples/generalfeatures/accessibility/defaultcs.aspx) demonstrates how you can make RadGrid accessible by leveraging the settings for the different caption, tooltip and summary properties of the rendered HTML elements.


|  **Property**  |  **Description**  |
| ------ | ------ |
| **GridButtonColumn.ToolTip** |Gets or sets the ToolTip property of each of the GridDataItem buttons.|
| **GridCheckBoxColumn.ToolTip** |Gets or sets the ToolTip property of each of the GridDataItem checkbox controls.|
| **GridEditCommandColumn.ToolTip** |Gets or sets the ToolTip property of each of the GridDataItem buttons.|
| **GridClientSelectColumn.ToolTip** |Properties that control the visual appearance of **RadGrid** and all tables in the hierarchy.|
| **RadGrid.PagerStyle.GoToPageTextBoxToolTip** |The ToolTip that will be applied to the GoToPage TextBox control.|
| **RadGrid.PagerStyle.GoToPageButtonToolTip** |The ToolTip that will be applied to the GoToPage input element.|
| **RadGrid.PagerStyle.ChangePageSizeTextBoxToolTip** |The ToolTip that will be applied to the ChangePageSize TextBox control.|
| **RadGrid.PagerStyle.ChangePageSizeButtonToolTip** |The ToolTip that will be applied to the ChangePageSize Button control.|
| **RadGrid.PagerStyle.ChangePageSizeComboBoxTableSummary** |The summary attribute that will be applied to the table which holds the ChangePageSize RadComboBox control.|
| **RadGrid.PagerStyle.ChangePageSizeComboBoxToolTip** |The ToolTip that will be applied to the input element in the ChangePageSize RadComboBox control.|
| **RadGrid.GridTableView.EditFormSettings.FormMainTableSummary** |The summary attribute for the table that wraps the whole GridEditFormItem.|
| **RadGrid.GridTableView.EditFormSettings.AutoGeneratedColumnEditorsTableWrapperSummary** |The summary attribute for the table which holds all cells created from the grid column editors GridEditFormItem|
| **RadGrid.GroupingSettings.MainTableSummary** |The summary attribute for the table that wraps the GridGroupPanel|
| **RadGrid.GroupingSettings.NestedTableSummary** |The summary attribute for the table second level table in the GridGroupPanel|
| **RadGrid.GroupingSettings.GroupItemsWrapperTableSummary** |The summary attribute for the table which holds all group items in the GridGroupPanel|
| **RadGrid.GroupingSettings.MainTableCaption** |The caption for the table that wraps the GridGroupPanel|
| **RadGrid.GroupingSettings.NestedTableCaption** |The caption for the table second level table in the GridGroupPanel|
| **RadGrid.GroupingSettings.GroupItemsWrapperTableCaption** |The caption for the table which holds all group items in the GridGroupPanel|
| **GridBoolColumnEditor.ToolTip** |The ToolTip that will be applied to the CheckBox control.|
| **GridTextColumnEditor.ToolTip** |The ToolTip that will be applied to the column editor initialized control.|

Covering this criterion is very important when you wouldlike to make your components accessible to people with disabilities.

The Section 508 standards are listed on the official government site:

[Section 508](http://www.section508.gov/)

Here are the code snippets from the aforementioned sample:

````ASP.NET
<head runat="server">
  <link type="text/css" rel="stylesheet" href="Skins/Sunset/Grid.Sunset.css" />
  <style type="text/css">.RadGrid_<%= MyGrid1.Skin %> th input
    {
         border:0px;         
         background-color: Transparent;         
         font-weight:bold;         
         cursor: pointer;         
         color:White;         
         text-align:left;        
    }        
    .RadGrid_<%= MyGrid1.Skin %> th, .RadGrid_<%= MyGrid1.Skin %> td         
    {
        white-space:nowrap;        
    }
  </style>
</head>
<body class="BODY">
  <form runat="server" id="mainForm" method="post" style="width: 100%;">
  <div>
    <telerik:MySection508Grid ID="MyGrid1" Skin="Sunset" DataSourceID="SqlDataSource1"
      AllowPaging="true" AllowSorting="true" runat="server" OnColumnCreated="MyGrid1_ColumnCreated">
      <mastertableview caption="Customers" summary="Customers">              
         <PagerTemplate>                
                    Change page:              
            <asp:Button ID="Button1" ToolTip="Previous Page" CommandName="Page" CommandArgument="Prev"CssClass="rgPagePrev" runat="server" />                    
            <asp:Button ID="Button2" ToolTip="Next Page" CommandName="Page" CommandArgument="Next" CssClass="rgPageNext" runat="server" />
         </PagerTemplate>         
      </mastertableview>
    </telerik:MySection508Grid>
    <asp:SqlDataSource ID="SqlDataSource1" runat="server" ConnectionString="<%$ ConnectionStrings:NorthwindConnectionString %>"
      ProviderName="System.Data.SqlClient" SelectCommand="SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address FROM Customers" />
  </div>
  </form>
</body>
````





````C#
protected void MyGrid1_ColumnCreated(object sender, GridColumnCreatedEventArgs e)
{     
    e.Column.HeaderButtonType = GridHeaderButtonType.PushButton;
}			
````
````VB
Protected Sub MyGrid1_ColumnCreated(ByVal sender As Object, ByVal e As Web.UI.GridColumnCreatedEventArgs) Handles MyGrid1.ColumnCreated
    e.Column.HeaderButtonType = Web.UI.GridHeaderButtonType.PushButton
End Sub
````




````C#
using Telerik.Web.UI;
namespace Telerik.Web.UI
{    
    public class MySection508Grid : RadGrid
    {       
        public MySection508Grid()
        {
        }    
        protected override void RegisterScriptControl()
        {                
        }
        protected override void RegisterScriptDescriptors()
        {            
        }
        protected override void RegisterCssReferences()
        {                 
        }
    }
}			
````
````VB
Imports Telerik.Web.UI
Namespace Telerik.Web.UI
 Public Class MySection508Grid Inherits RadGrid
            Public Sub New()
            End Sub
            Protected Overloads Overrides Sub RegisterScriptControl()
            End Sub
            Protected Overloads Overrides Sub RegisterScriptDescriptors()
            End Sub
            Protected Overloads Overrides Sub RegisterCssReferences()
            End Sub
        End Class
    End Namespace
````

