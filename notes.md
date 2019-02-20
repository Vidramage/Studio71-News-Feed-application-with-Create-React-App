This application is a demo for feed application supported by studio 71.

First, you have to install `semantic-ui-react`, `semantic-ui-css` package with yarn or npm

```
yarn add semantic-ui-react
yarn add semantic-ui-css
```
```
npm install semantic-ui-react --save
npm install semantic-ui-css --save
```

Import css for semantic UI to App.js
```
import 'semantic-ui-css/semantic.min.css';
```

In home/index.js,
```
import {
    Icon,
    Container,
    Feed,
    Table
} from 'semantic-ui-react';
```

Then, you have to implement feed like this
```
<Feed.Event>
    <Feed.Label>
        {item.thumb_url_default || item.thumbnail ?
            <img src={item.thumbnail ? item.thumbnail : item.thumb_url_default} /> :
            <Icon disabled name='user' /> }
    </Feed.Label>
    <Feed.Content>
        <Feed.Summary>
            <Feed.User>{item.name}</Feed.User>
            <Feed.Date>{item.timeframe} Ago</Feed.Date>
        </Feed.Summary>
        <Feed.Extra text>
            <p>Message: {item.message}</p>
            <Table celled padded size='small'>
                <Table.Header>
                    <Table.Row>
                        <Table.HeaderCell>Est Subs</Table.HeaderCell>
                        <Table.HeaderCell>Mod 7 days</Table.HeaderCell>
                        <Table.HeaderCell>CMS</Table.HeaderCell>
                        <Table.HeaderCell>Subscribers</Table.HeaderCell>
                        <Table.HeaderCell>Estimated Subscribers 30 days</Table.HeaderCell>
                        <Table.HeaderCell>Domain</Table.HeaderCell>
                        <Table.HeaderCell>Estimated Subscribers 7 days</Table.HeaderCell>
                        <Table.HeaderCell>Mod 30 days</Table.HeaderCell>
                        <Table.HeaderCell>Type</Table.HeaderCell>
                        <Table.HeaderCell>Title</Table.HeaderCell>
                    </Table.Row>
                </Table.Header>
                    <Table.Body>
                    <Table.Row>
                        <Table.Cell>{item.est_subs}</Table.Cell>
                        <Table.Cell>{item.mod_7_days}</Table.Cell>
                        <Table.Cell>{item.cms}</Table.Cell>
                        <Table.Cell>{item.subscribers}</Table.Cell>
                        <Table.Cell>{item.estimated_subscribers_30_days}</Table.Cell>
                        <Table.Cell><Icon disabled name='youtube' size='huge' color='red' /></Table.Cell>
                        <Table.Cell>{item.estimated_subscribers_7_days}</Table.Cell>
                        <Table.Cell>{item.mod_30_days}</Table.Cell>
                        <Table.Cell>{item.type}</Table.Cell>
                        <Table.Cell>{item.title}</Table.Cell>
                    </Table.Row>
                </Table.Body>
            </Table>
        </Feed.Extra>
        <Feed.Meta>
            <Feed.Like>
                <Icon name='like' />
                    4 Likes
            </Feed.Like>
        </Feed.Meta>
    </Feed.Content>
</Feed.Event>
```

I wanted to very briefly explain each step and how I iterated over each design phase with images to accompany the description and how I approached making this design. I noticed that making an API call to the link provided was not possible because of Cross Origin blocking me from accessing it directly on your server side, so I created a javascript data.json file and used axios to fetch the static file and render that.

My thought process was that I had a set of data to work with but no direction as far as design or user experience was concerned or how the data was to be displayed. I originally started with a layout that displayed 7 cards per row with 3 rows in total. Image: https://i.imgur.com/gIPvJIf.jpg

The next iteration of design was recreating the data into a news-feed type format which is already nicely supplied by semantic-UI, and some slight initial changes were made as to how and which data was being displayed. Image: https://i.imgur.com/OhKqqL8.jpg

The third iteration of the design I decided it would be best to organize the data into a table so it was more easily organized and easier for people to visually see. Image: https://i.imgur.com/8L83ZcL.jpg

The fourth iteration called for adding the youtube logo for the "domain" section as a nice styling touch as well as adding additional data that the viewer of the feed would be able to see. As you can see we increased the viewable data to 10 individual content areas all of which are taken directly from the static data.json file. Image: https://i.imgur.com/U2bDm8D.jpg

The final design included making the tables all the same size so we had a consistent, stylized and organized way to display all of our data to the end user in the news feed. Image: https://i.imgur.com/0UfiI5t.jpg