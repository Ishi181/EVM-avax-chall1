// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract smartProject {

    address public teacher;
    
    uint256 public marks;

    constructor() {
        teacher = msg.sender;
    }

    function setMarks(uint256 _marks) public {
        require(_marks < 90 , "Marks can't be more than 90. ");
        marks = _marks;
    }

    function checkTeacher() public view {
        assert(teacher == msg.sender);
    }

    function modifymarks() public {
        if(msg.sender != teacher) {
            revert("Only teacher can modify the marks. ");
        }
        marks = 10;
    }
   
}
