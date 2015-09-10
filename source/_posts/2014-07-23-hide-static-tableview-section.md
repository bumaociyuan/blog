---
layout: post
title:  "hide static tableview section"
date:   2014-07-23 09:08:00
categories: ios
tags: [code snippet]

---

主要是实现以下几个方法

```
-(UIView*)tableView:(UITableView *)tableView viewForHeaderInSection:(NSInteger)section
{
    if(section == 1 && hideTableSection)
        return [[UIView alloc] initWithFrame:CGRectZero];   
    return nil; 
}

- (CGFloat)tableView:(UITableView *)tableView heightForHeaderInSection:(NSInteger)section
{
    if(section == 1 && hideTableSection)
        return 1;
    return 32;
}

-(CGFloat)tableView:(UITableView *)tableView heightForFooterInSection:(NSInteger)section
{
    if(section == 1 && hideTableSection)
        return 1;
    return 16;
}

-(UIView*)tableView:(UITableView *)tableView viewForFooterInSection:(NSInteger)section
{
    if(section == 1 && hideTableSection)
        return [[UIView alloc] initWithFrame:CGRectZero];    
    return nil;
}

- (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section
{
    if(section == 1)
    {
        if(hideTableSection)
            return 0;
        else
            return 1;
    }
    else
    {
        return 2;
    }
}

```