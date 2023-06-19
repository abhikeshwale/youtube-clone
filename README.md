side bar js
import React from 'react';
import { useSelector } from 'react-redux';
import store from '../Utils/store';

const Sidebar = () => {
  const isMenuOpen = useSelector(store => store.app.isMenuOpen);
  if(!isMenuOpen) return null;
  //early return
  return (
    <div className="p-5 shadow-lg w-48">
      <ul>
        <li>Home</li>
        <li>Shorts</li>
        <li>Videos</li>
        <li>Live</li>
      </ul>
      <h1 className="font-bold  pt-5">Subscriptions</h1>
      <ul>
        <li>Music</li>
        <li>Sports</li>
        <li>Gaming</li>
        <li>Movies</li>
      </ul>

      <h1 className="font-bold pt-5">Watch Later</h1>
      <ul>
        <li>Music</li>
        <li>Sports</li>
        <li>Gaming</li>
        <li>Movies</li>
      </ul>
    </div>
  );
};

export default Sidebar;




head js
import React from "react";
import MenuRoundedIcon from "@mui/icons-material/MenuRounded";
import SearchRoundedIcon from "@mui/icons-material/SearchRounded";
import PersonOutlineRoundedIcon from "@mui/icons-material/PersonOutlineRounded";
import { useDispatch } from "react-redux";
import { toggleMenu } from "../Utils/appSlice";

const Head = () => {
  const dispatch = useDispatch();
  const toggleMenuHandler = () => {
    dispatch(toggleMenu());
  };
  return (
    <div className="grid grid-flow-col p-5 m-2 shadow-lg">
      <div className="flex col-span-1">
        <MenuRoundedIcon
          className="h-8 cursor-pointer"
          onClick={() => toggleMenuHandler()}
        />
        <img
          className="h-8 mx-2"
          alt="yt-logo"
          src="https://www.gstatic.com/youtube/img/branding/youtubelogo/svg/youtubelogo.svg"
        />
      </div>
      <div className="col-span-10 text-center">
        <input
          type="text"
          className="w-1/2 border border-grey-400 p-2 rounded-l-full"
        ></input>
        <button className="border border-grey-400 p-2 rounded-r-full">
          Search
        </button>
      </div>

      <div>
        <PersonOutlineRoundedIcon className="h-8" />
      </div>
    </div>
  );
};

export default Head;


ap slic ejs

import { createSlice } from '@reduxjs/toolkit';

const appSlice = createSlice({
  name: "app",
  initialState: {
    isMenuOpen: true,
  },
  reducers: {
    toggleMenu: (state) => {
      state.isMenuOpen = !state.isMenuOpen;
    },
  },
});

export const { toggleMenu } = appSlice.actions;
export default appSlice.reducer;


store js
import { configureStore } from '@reduxjs/toolkit';
import appSlice from "./appSlice"
const store = configureStore({
  reducer: {
    app: appSlice,
  },
});

export default store;
