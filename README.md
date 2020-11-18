# Neighbor hoods
 
function neighborhoods(input) {
    let neighborhood = input.shift().split(`, `);
    let listOfNames = input;
    let listOfNeighborhood = {};
    neighborhood.forEach(element => {
        if (!listOfNeighborhood.hasOwnProperty(element)) {
            listOfNeighborhood[element] = [];
        }
    })
    listOfNames.forEach(element => {
        element = element.split(` - `);
        let [neighbor, name] = element;
        if (listOfNeighborhood.hasOwnProperty(neighbor)) {
            listOfNeighborhood[neighbor].push(name);
        }
    })

    let sorted = Object.entries(listOfNeighborhood);
    sorted.sort((a, b) => b[1].length - a[1].length);
    sorted.forEach(element=>{
        let[streetName, list] = element;
        console.log(`${streetName}: ${list.length}`);
        list.forEach(token=>{
            console.log(`--${token}`);
        })
    })
}
