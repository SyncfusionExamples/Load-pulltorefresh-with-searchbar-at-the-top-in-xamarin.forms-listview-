# Pull-to-refresh with SearchBar at Top

When the SearchBar or any view placed above the [PullToRefresh](https://help.syncfusion.com/cr/cref_files/xamarin/Syncfusion.SfPullToRefresh.XForms~Syncfusion.SfPullToRefresh.XForms.SfPullToRefresh.html) control, pulling action does not work on the SfListView because touches directly passed to the ListView instead of SfPullToRefresh control. You can overcome this problem by placing the SfListView inside the Grid and place that Grid as [PullToRefresh.PullableContent](https://help.syncfusion.com/cr/cref_files/xamarin/Syncfusion.SfPullToRefresh.XForms~Syncfusion.SfPullToRefresh.XForms.SfPullToRefresh~PullableContent.html).

```
<ContentPage xmlns:pulltoRefresh="clr-namespace:Syncfusion.SfPullToRefresh.XForms;assembly=Syncfusion.SfPullToRefresh.XForms"
             xmlns:syncfusion="clr-namespace:Syncfusion.ListView.XForms;assembly=Syncfusion.SfListView.XForms" >
  <ContentPage.Content>
        <Grid RowSpacing="0" ColumnSpacing="0" Padding="0" Margin="0">
            <Grid.RowDefinitions>
                <RowDefinition Height="50" />
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid.Behaviors>
                <local:SfListViewPullToRefreshBehavior />
            </Grid.Behaviors>
            <SearchBar x:Name="filterText" Placeholder="Search" FontSize="14" />
  
            <pulltoRefresh:SfPullToRefresh x:Name="pullToRefresh" Grid.Row="1"
                                           ProgressBackgroundColor="#428BCA" RefreshContentHeight="50" 
                                           RefreshContentWidth="50" TransitionMode="Push" IsRefreshing="False">
                <pulltoRefresh:SfPullToRefresh.PullableContent>
                    <Grid>
                        <syncfusion:SfListView x:Name="listView" AllowSwiping="True"
                                   AutoFitMode="Height">
                        </syncfusion:SfListView>
                    </Grid>
                </pulltoRefresh:SfPullToRefresh.PullableContent>
            </pulltoRefresh:SfPullToRefresh>
        </Grid>
    </ContentPage.Content>
</ContentPage>
```
To know more about PullToRefresh in ListView, please refer our documentation [here](https://help.syncfusion.com/xamarin/sflistview/pull-to-refresh).