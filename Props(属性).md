# Props（属性）

大多数组件在创建时就可以使用各种参数来进行定制。用于定制的这些参数就称为props（属性）。

以常见的基础组件Image为例，在创建一个图片时，可以传入一个名为source的 prop 来指定要显示的图片的地址，以及使用名为style的 prop 来控制其尺寸。

    import React, { Component } from 'react';
    import { Image } from 'react-native';

    export default class Bananas extends Component {
    render() {
        let pic = {
        uri: 'https://upload.wikimedia.org/wikipedia/commons/d/de/Bananavarieties.jpg'
        };
        return (
        <Image source={pic} style={{width: 193, height: 110}} />
        );
    }
    }


请注意{pic}外围有一层括号，我们需要用括号来把pic这个变量嵌入到 JSX 语句中。括号的意思是括号内部为一个 js 变量或表达式，需要执行后取值。因此我们可以把任意合法的 JavaScript 表达式通过括号嵌入到 JSX 语句中。

自定义的组件也可以使用props。通过在不同的场景使用不同的属性定制，可以尽量提高自定义组件的复用范畴。只需在render函数中引用this.props，然后按需处理即可。下面是一个例子


    import React, { Component } from 'react';
    import { Text, View } from 'react-native';

    class Greeting extends Component {
    render() {
        return (
        <View style={{alignItems: 'center', marginTop: 50}}>
            <Text>Hello {this.props.name}!</Text>
        </View>
        );
    }
    }

    export default class LotsOfGreetings extends Component {
    render() {
        return (
        <View style={{alignItems: 'center'}}>
            <Greeting name='Rexxar' />
            <Greeting name='Jaina' />
            <Greeting name='Valeera' />
        </View>
        );
    }
    }


